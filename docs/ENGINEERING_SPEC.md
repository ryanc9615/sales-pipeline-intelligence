# Sales Pipeline Intelligence Tool — Engineering Specification

**Version:** V1 planning baseline  
**Prepared:** 31 October 2026  
**Implementation status:** NOT STARTED  
**Primary goal:** Build and independently explain a useful data application from an ambiguous commercial question to a deployed, tested dashboard.

## 1. User, problem and outcome

The user is a sales manager at a fictional B2B business. CRM exports contain opportunities, but it is difficult to tell which pipeline is credible, which deals need action and whether the current reporting period's target is covered.

**User story:** “I upload a CSV export, confirm its snapshot date and reporting period, and see a clear picture of current pipeline, closed win rate, conversion, deal risks and an assumption-based bookings forecast. I can inspect the deals behind each number.”

The V1 workflow is: choose bundled synthetic data or upload one CSV; validate the complete file; choose analysis controls; calculate reproducible metrics; display summaries, charts, deal-level risks and calculation definitions. Invalid data blocks analysis until corrected.

## 2. Scope, constraints and priorities

| Area | V1 decision / constraint |
|---|---|
| Learning budget | Three-week target; approximately 40 focused hours, 36–48 planning range |
| Stack | Python 3.12 baseline, pandas, Streamlit, pytest, Git; verify the installed interpreter before setup |
| Data | One current-state CSV snapshot, one row per opportunity; no joins or event history |
| Business | One fictional business, GBP, one consistent amount basis: total deal contract value |
| Capacity | At most 10,000 data rows and 5 MiB (5,242,880 bytes) per upload |
| Runtime | One Python application, one Streamlit entry point; no database or separate application API |
| Deployment | Aim for Streamlit Community Cloud; confirm current requirements at Phase 08 |
| Spend | Aim for no paid infrastructure; do not purchase hosting or subscriptions without a new user instruction |
| Data handling | Synthetic data for the public portfolio; uploaded data processed in session memory, without intentional persistence |
| Performance | Measure a 10,000-row local run; aim for validation + calculations within 5 seconds on the learner's machine; record actual results and hardware |
| Delivery priority | Correctness and explainability → complete workflow → deployment → visual polish |

**In scope:** strict CSV ingestion; a data dictionary; explicit validation; core pandas transformations; current pipeline totals and stage distribution; closed win rate and observed creation-cohort conversion; won-deal sales-cycle median; overdue, stalled and missing-activity flags; probability-weighted bookings forecast; coverage against remaining target; simple owner filtering; sample data; unit/integration tests; one local HTTP/JSON learning exercise; a public synthetic-data demo; three evidence-based sales insights.

**PARK FOR LATER:** Salesforce/HubSpot connectors, OAuth, API keys, live CRM sync, arbitrary column mapping, stage event histories, historical pipeline reconstruction, multi-currency, multiple pipelines, accounting revenue recognition, subscriptions/ARR, renewal cohorts, commission models, AI/LLMs, ML predictions, causal claims, authentication, paid billing, databases, FastAPI services, microservices, Docker/Kubernetes, advanced CI/CD and a React frontend.

The application must remain usable without a live API. The HTTP exercise teaches transport and contracts; it is not a CRM integration.

## 3. Canonical CSV contract

Accept comma-delimited UTF-8 / UTF-8 with BOM, with a header row and standard CSV quoting. Reject unreadable encoding, malformed CSV, duplicate header names after trimming, missing required headers, too many rows, oversized files and header-only files. Ignore extra columns after displaying their names as unused. Do not silently guess delimiters or dates.

Read raw fields as strings first. Preserve identifiers such as `0007` and literal `NA`; only an empty/whitespace-only cell is missing. Strip surrounding whitespace from headers and values. Headers must match the names below after trimming. Lowercase stage values and currency-uppercase conversion are permitted normalisations; do not invent aliases or fix spelling silently.

| Required header | Value rule | Purpose |
|---|---|---|
| `deal_id` | Nonempty string, unique after trimming; preserve leading zeros | Stable row identity |
| `deal_name` | Nonempty string | Human-readable opportunity |
| `owner` | Nonempty string, case-sensitive after trimming | Global owner filter |
| `stage` | One of the six canonical values below | Current state and default probability |
| `amount` | Plain decimal GBP amount, >0 and ≤999999999.99; at most 2 decimal places; no currency sign, thousands separators, exponent, NaN or infinity | Total contract value |
| `currency` | `GBP` after uppercase conversion; every row must match | Prevent mixed-currency aggregation |
| `created_date` | Required ISO `YYYY-MM-DD`, real calendar date, ≤snapshot date | Creation cohort and cycle start |
| `expected_close_date` | Required for open deals; may be blank for closed deals; if supplied, ≥created date; may be after snapshot date | Open-deal forecast timing |
| `actual_close_date` | Required for closed deals, blank for open deals; created date ≤value≤snapshot date | Actual outcome period |
| `stage_entered_date` | Required for open deals; created date≤value≤snapshot date; optional for closed deals, and if supplied must be ≤actual close date | Current-stage aging |
| `last_activity_date` | May be blank; if supplied, created date≤value≤snapshot date | Inactivity / missing-data flag |

All 11 headers are required even where a cell may be blank. Dates are date-only; no ambiguous local date formats or timezones. Missing expected-close dates on open deals block analysis; missing activity dates are allowed and visible. Do not silently discard bad rows, deduplicate deals or impute dates.

### Stage and probability map

| Canonical stage | Open / closed | Default probability |
|---|---|---:|
| `qualification` | Open | 0.10 |
| `discovery` | Open | 0.25 |
| `proposal` | Open | 0.50 |
| `negotiation` | Open | 0.75 |
| `closed_won` | Closed | 1.00 |
| `closed_lost` | Closed | 0.00 |

These are **illustrative assumptions**, not empirically calibrated win probabilities. The UI lets the user edit the four open-stage probabilities in [0,1]; show the active values with the forecast. Closed outcomes remain 1 and 0. Do not infer probabilities from the same small snapshot or claim forecast accuracy.

Derive open/closed status from `stage`; do not accept a conflicting second status column.

## 4. Analysis controls and scope

Require an explicit **CSV snapshot date**. The bundled dataset declares 2026-10-31. For a new upload, ask the user to confirm its actual snapshot date; do not silently substitute today's date. The date is a declared cutoff, not a historical time-travel control. A current-stage export cannot reconstruct earlier pipeline states.

The reporting period uses inclusive calendar dates and must satisfy `period_start ≤ snapshot_date ≤ period_end`. Default the bundled demo to 2026-10-01 through 2026-12-31. Restrict V1 to the current reporting period; completed-period and multi-period forecasting are deferred.

Other controls: owner multiselect (default all); positive GBP period bookings target (default £100,000 for the reference case); four open-stage probabilities. Use fixed documented risk thresholds in V1: 14 inactive days and 30 days in the current stage. Threshold configurability is optional only if time remains after all delivery gates.

Apply the owner selection **before every calculation**, including closed outcomes, risks, forecast and coverage. The target is manually entered for the selected scope; on an owner-filter change, require target reconfirmation before showing coverage. If no owners are selected, show an empty result and prompt for a selection. Do not add a global stage filter that accidentally removes closed deals from win-rate denominators.

Some cards describe the entire current open pipeline; others describe the selected reporting period. Put the scope in the label rather than forcing every measure onto an inappropriate date field.

## 5. Money, dates and deterministic arithmetic

- Validate amounts using `Decimal` constructed from the original string; store canonical money as integer pence (`amount_pence`). Do not parse money through binary float.
- Represent stage probabilities as `Decimal` from strings. Weighted pence for each deal are `amount_pence × probability`, rounded to a whole penny with `ROUND_HALF_UP`. **Sum the rounded deal values**. Do not substitute rounding only the final total.
- Counts are integers. Ratios may use normal numeric division for display; use an explicit denominator-zero branch. `None` / N/A is distinct from zero.
- Parse date columns explicitly and compare dates consistently. Pass snapshot date, reporting period and configuration into functions; no hidden call to today's date inside calculations.
- Do not mutate the caller's input DataFrame. Identical validated data and controls must yield identical results.
- Format pounds and percentages at the presentation boundary. Keep numeric values available for checks.

## 6. Metric definitions — the calculation contract

Let `S` be all validated rows after the owner filter. `O` is its open deals. `W` and `L` are its `closed_won` and `closed_lost` rows. `P` is the inclusive reporting period; `A` is the snapshot date.

| Metric / label | Exact rule | Empty / boundary behaviour |
|---|---|---|
| Current open pipeline | Sum amount for every deal in `O`, irrespective of expected close period | 0 for no open deals |
| Current open deal count | Number of rows in `O` | 0 |
| Pipeline by current stage | Count and unweighted amount in `O`, grouped in canonical stage order | Include zero-value stages |
| Weighted current open pipeline | Sum per-deal rounded weighted amounts for all `O` | 0; **not** the period forecast |
| Closed-deal win rate (count) | Count of `W` with actual close in `P` ÷ count of `W ∪ L` with actual close in `P` | N/A when no deals closed in `P`; show numerator and denominator |
| Observed creation-cohort conversion (count) | Count of current `W` with created date in `P` ÷ count of all `S` with created date in `P` | N/A for empty cohort; show still-open cohort count and “outcomes incomplete” |
| Won-deal median sales cycle | Median of `(actual_close_date − created_date).days` for `W` with actual close in `P` | N/A with no wins; same-day close is 0 days; do not include lost/open deals |
| Actual won bookings in period | Sum amounts for `W` with actual close in `P` | 0; not recognised revenue |
| Eligible open period pipeline | Open deals with `max(A, period_start) ≤ expected_close_date ≤ period_end` | Excludes overdue deals and out-of-period deals |
| Weighted open period forecast | Sum per-deal rounded weighted amounts for eligible open period deals | 0 if none |
| Total period bookings forecast | Actual won bookings in period + weighted open period forecast | Won deals counted once; lost deals contribute 0 |
| Remaining period target | `max(period_target − actual_won_bookings, 0)` | Target itself must be positive |
| Remaining-target pipeline coverage | Unweighted eligible open period pipeline ÷ remaining period target | N/A, label “target met”, when remaining target is 0 |
| Forecast gap to target | `period_target − total_period_bookings_forecast` | Positive = shortfall; negative = forecast above target |

The creation cohort is defined by creation date, even when a won outcome closed in a later part of the period. Open deals are not treated as losses. Explain maturity bias: a recent cohort has not had equal time to close. V1 cannot calculate true stage-to-stage conversion, stage progression, time spent in prior stages or historical slippage from a snapshot.

Do not assume coverage must be a universal 3× or 4× ratio. The appropriate level depends on win probability, deal timing and the business. Do not call a weighted forecast a statistical confidence interval or a promise.

## 7. Risk flags and sales actions

Evaluate risks for open deals only, across the entire current open pipeline after owner filtering.

- `inactive_days = (A − last_activity_date).days` when the date exists; otherwise missing / N/A.
- `stage_age_days = (A − stage_entered_date).days`.
- `overdue = expected_close_date < A`. A deal due on the snapshot date is not overdue.
- `inactive = inactive_days ≥ 14` when activity exists; false when missing, with a separate flag.
- `stage_stalled = stage_age_days ≥ 30`.
- `stalled = inactive OR stage_stalled`.
- `missing_activity = last_activity_date is blank`.
- `at_risk = overdue OR stalled OR missing_activity`.

A missing activity date is a data-quality uncertainty, not proof that no activity occurred. A stalled flag is a review heuristic, not proof a deal will be lost. A deal may carry several flags; count each deal once in an aggregate at-risk amount. Keep individual flags visible so overlapping subtotals are not mistaken for additive totals.

Flagged deals remain in the probability-weighted forecast **if otherwise eligible**. Do not silently reduce their probabilities. Overdue deals are excluded from the forward open-period forecast by the timing rule, but remain in current pipeline and risks. Never roll overdue expected dates forward automatically.

## 8. Architecture and repository boundaries

Use the simplest modules that earn their place. This is a target map, not an instruction to create empty modules at Phase 00.

| Target path | Responsibility / boundary |
|---|---|
| `streamlit_app.py` | Widgets, user messages, layout and formatting; no business formulas |
| `app/__init__.py`, `app/__main__.py` | Package marker and initial environment smoke entry point |
| `app/loaders.py` | File bytes, header checks, parsing, provenance; no UI imports |
| `app/validation.py` | Schema, row/date/money checks and structured errors |
| `app/metrics.py` | Pipeline, conversion, cycle and risk calculations on validated data |
| `app/forecasts.py` | Weights, eligible timing, period forecast and coverage |
| `tests/` | Independent reference-case, boundary and integration tests |
| `data/samples/` | Synthetic CRM CSV and README defining snapshot/date/amount basis |
| `data/fixtures/` | Small hand-checkable dataset and deliberately invalid test fixtures |
| `examples/api/` | Local JSON fixture and small read-only HTTP exercise, not deployed |
| `docs/`, `prompts/` | Scope, decisions, evidence and tutoring continuity |
| `requirements.txt` | Exact tested runtime package versions |
| `requirements-dev.txt` | Runtime requirements plus exact tested pytest version |
| `.streamlit/config.toml` | Add only when needed for upload size / deployment settings |

Processing boundary: raw bytes → validated canonical DataFrame → calculation functions → result values / deal-level flags → Streamlit rendering. Calculation functions must run and be tested without Streamlit, network calls or filesystem access. pandas is allowed in these functions. Add classes only for a demonstrated need; dictionaries and clear functions are adequate.

## 9. Data quality, provenance and error handling

Return errors with record number, column and a short corrective message. Use data-record numbering (first data row = 1), so a quoted field with a newline cannot make the reported record ambiguous. File-level errors need no record number. Show at most the first 50 detailed errors plus the total count; block all KPI rendering on any hard error.

Record the source filename, SHA-256 of the original bytes, row count, snapshot date, owner filter, reporting period, target and probabilities with the analysis metadata. These describe how the output was obtained; do not log the actual CRM rows.

If an upload fails, do not leave the previous dataset's KPIs visible under the new filename. Distinguish empty-valid owner selection from an invalid upload. Show user-friendly errors rather than a traceback in the UI; retain useful local development diagnostics.

The bundled synthetic-data route and upload route must feed the same validator and calculator. Do not hardcode sample headline outputs.

## 10. Dashboard acceptance

One Streamlit application with three compact views or tabs is enough:

1. **Overview:** source/date/scope, current pipeline cards, stage amount/count chart, closed win rate with counts, creation-cohort conversion and open-cohort count, median sales cycle.
2. **Deal review:** overdue/stalled/missing-activity summary and a deal table with owner, stage, amount, relevant dates, age and individual flags; at-risk union totals without double counting.
3. **Forecast:** period and target controls, active stage probabilities, actual won + weighted open = total forecast bridge, remaining-target coverage and forecast gap. Include the eligible deal table so the calculation can be traced.

Provide a clear empty state, invalid-upload state, sample-data entry point and short metric definitions. Every amount/rate must reconcile to its underlying rows. Streamlit's built-in charts/table widgets are sufficient; avoid a new chart library unless a concrete need emerges.

## 11. API fundamentals requirement

At Phase 07, create a JSON file containing a small synthetic array of canonical deal records. Serve **only** `examples/api/` on localhost, for example `python -m http.server 8000 --bind 127.0.0.1 --directory examples/api`. Fetch it with `urllib.request` using an explicit timeout; inspect method, URL/port/path, status, content type and decoded JSON. Trigger and handle a missing-path 404, and explain the difference between an HTTP failure and a valid response with an invalid business schema.

Pass a valid decoded records array through the same validation rules and compare calculations with the equivalent small CSV fixture. This exercise can remain a script; it does not add API upload support to the public UI. Stop the local server afterwards. Do not serve the repository root or use Python's simple HTTP server as production hosting.

Record why real CRM APIs later need authentication, pagination, rate-limit handling, field mapping and snapshot consistency. Do not implement those features in V1. This is an API-consumption learning exercise, not evidence of a full REST backend.

## 12. Verification and delivery

Required tests verify independent outcomes rather than reproducing the production algorithm. Use the hand-derived values in `CALCULATION_EXAMPLES.md`. Cover:

- Full reference case: pipeline, stage totals, win rate, cohort conversion, cycle median, risk union, timing, weighted forecast and coverage.
- Monetary precision, rounding per deal and summation; rates of 0 and 1; target met / exceeded; no eligible pipeline.
- Blank activity; exactly 14 inactive days / 30 stage days; expected close equal to snapshot and period end; next-day-outside-period exclusion.
- Empty closed denominator, empty cohort, all-open, all-closed and no selected owners; totals are 0 and undefined rates are N/A.
- Missing/duplicate headers, duplicate IDs, leading-zero ID, literal `NA`, malformed money/dates, mixed currency, inconsistent closed dates, too-large uploads, row limit and malformed CSV.
- CSV bytes through loader, validation and calculations as an integration test; invalid data yields no partial analysis; repeated runs do not mutate input.
- Manual UI checks for bundled data, valid upload, invalid upload after a valid one, owner filter/target reconfirmation and formula explanations.

Use pytest for calculations and boundary contracts; a small manual UI checklist is sufficient. Do not build a browser-test framework or chase an arbitrary coverage percentage.

At Phase 08, install from recorded dependencies in a clean environment, run the relevant tests, launch the app and deploy the synthetic portfolio demo. Record the live URL, commit, Python/package versions, executed commands, dated outcomes and any limitations. Check the live sample flow and a synthetic upload from a fresh browser session. A local launch is not deployment evidence.

For the public demo: make the synthetic-data scope clear; do not intentionally write uploaded files to disk or use shared/global caching for uploaded data; do not commit secrets or client exports. No accounts or persistent history are required. Current hosting capabilities and pricing must be rechecked at deployment time; a fallback host does not justify expanding the architecture.

## 13. Final acceptance gate

- [ ] A live dashboard is reachable and demonstrates the complete synthetic-data workflow.
- [ ] Canonical sample data, data dictionary and snapshot date are supplied.
- [ ] Bad input produces actionable validation errors and no misleading KPIs.
- [ ] All specified metrics match independently derived values and relevant tests have actually passed.
- [ ] Period forecast and remaining-target coverage use the documented eligibility rules; money reconciles to individual deals.
- [ ] Forecast assumptions, cohort limitations and bookings/revenue distinction are visible.
- [ ] API/HTTP exercise and observed 200/404 outcomes are documented accurately.
- [ ] Clean setup and deployment steps work at a recorded commit.
- [ ] Three actionable insights link numbers → commercial implication → proposed action → caveat / follow-up.
- [ ] The learner can trace a deal through the application, modify a rule and diagnose an injected bug without relying on a full AI-generated replacement.

## 14. Official technical references

Checked while preparing this baseline on 31 October 2026; recheck changing deployment details during Phase 08. Read the relevant section when needed, not as an upfront course.

- [Python virtual environments](https://docs.python.org/3.12/library/venv.html)
- [Python Decimal arithmetic and rounding](https://docs.python.org/3.12/library/decimal.html)
- [pandas CSV loading](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)
- [Streamlit file upload](https://docs.streamlit.io/develop/api-reference/widgets/st.file_uploader)
- [Streamlit deployment](https://docs.streamlit.io/deploy/streamlit-community-cloud/deploy-your-app/deploy)
- [Streamlit dependency configuration](https://docs.streamlit.io/deploy/streamlit-community-cloud/deploy-your-app/app-dependencies)
- [pytest getting started](https://docs.pytest.org/en/stable/getting-started.html)
- [Python HTTP client](https://docs.python.org/3.12/library/urllib.request.html) and [local HTTP server](https://docs.python.org/3.12/library/http.server.html)
