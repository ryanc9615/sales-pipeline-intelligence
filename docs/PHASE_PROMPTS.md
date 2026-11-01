# Guided Conversation Prompts — Sales Pipeline Intelligence Tool

Use one phase prompt per guided conversation. Follow the latest repository project state; these prompts do not establish that any phase is implemented. Individual copies are included in `prompts/` in the starter/reference archives.

# Phase 00 — Setup and Development Workflow

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 00 — Setup and Development Workflow**, milestone **1 — Trustworthy data and baseline metrics**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Create and understand a clean local Python development environment and a reproducible Git workflow before adding analytics.

**Prerequisites:** No earlier phase; preserve the starter documents.

**Guide these activities one meaningful step at a time:**

1. Inspect the actual folder, operating system, terminal, editor, Python interpreter and Git state. Do not assume another project's settings apply.
2. Create a project-specific virtual environment; identify its interpreter and explain package isolation.
3. Review the existing documents and .gitignore. Create only a minimal app package / smoke entry point when needed.
4. Run python -m app, inspect the output and make a meaningful local Git commit after reviewing the staged diff.
5. Record actual environment evidence and the next action in docs/PROJECT_STATE.md. Add packages only when a later phase needs them.

**Technical concepts:** interpreter, venv, modules/packages/imports, terminal working directory, dependency declaration, Git working tree/staging/commit.

**Commercial concepts:** reproducibility and evidence before assuming a report can be trusted.

**Acceptance evidence:**

- [ ] A small package entry point actually runs in the project environment.
- [ ] I can identify the active interpreter and explain the venv.
- [ ] The first meaningful local commit and working-tree state are verified.
- [ ] The handoff separates observed setup from unimplemented functionality.

**Out of scope:** No CSV loader, analytics formulas, pandas transformations, Streamlit UI, database or live integration.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Help me inspect my actual project folder and local environment, then guide only the first useful setup step.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 01 — Sales Domain, Data Contract and Manual Examples

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 01 — Sales Domain, Data Contract and Manual Examples**, milestone **1 — Trustworthy data and baseline metrics**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Translate the commercial brief into precise data and calculation semantics before implementing formulas.

**Prerequisites:** Phase 00 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Explain opportunities, stage versus status, bookings versus recognised revenue, target scope and the three relevant date roles.
2. Read the canonical CSV contract and decide how raw strings become dates, integer pence and canonical stages.
3. Work the eight-deal reference case by hand: current pipeline, closed win rate, observed cohort conversion and cycle median.
4. Distinguish snapshot-supported metrics from stage-to-stage conversion and historical pipeline reconstruction.
5. Sketch the smallest data flow and note any real ambiguity in docs/DECISIONS.md without enlarging scope.

**Technical concepts:** data contracts, dictionaries/records, types, nullable values, invariants, pure inputs/outputs.

**Commercial concepts:** sales stages, outcome denominators, cohort maturity, contract value, snapshot timing.

**Acceptance evidence:**

- [ ] All 11 fields and conditional date rules can be explained.
- [ ] The reference £110k open pipeline, 2/3 win rate, 1/2 cohort conversion and 29.5-day median are derived independently.
- [ ] I can explain why a snapshot cannot show stage-to-stage conversion.
- [ ] The amount basis and snapshot date are explicit.

**Out of scope:** No dashboard, database, advanced object model or full metric implementation.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Ask me to explain the difference between created, expected-close and actual-close dates using one reference deal.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 02 — CSV Ingestion, Validation and Sample Data

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 02 — CSV Ingestion, Validation and Sample Data**, milestone **1 — Trustworthy data and baseline metrics**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Turn raw CSV bytes into canonical validated data or precise actionable errors, without silently repairing records.

**Prerequisites:** Phase 01 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Introduce pandas only as needed. Inspect headers before automatic renaming can hide duplicates; preserve IDs and literal NA values.
2. Implement file, schema, row, stage, GBP money and conditional date rules in small increments.
3. Return useful record/column errors and block all analysis when any hard error exists; allow blank activity with a visible missing flag.
4. Create the eight-deal golden CSV plus deliberately invalid tiny fixtures. Then create a deterministic 100–200-row fictional demo with varied stages, owners, outcomes and risks.
5. Record the sample snapshot date, generation method and amount basis. Add provenance and meaningful validation tests, including limit boundaries.

**Technical concepts:** CSV parsing, bytes/text, pandas dtypes, string-to-type conversion, validation boundaries, errors, fixtures, deterministic sample generation.

**Commercial concepts:** data quality, one row per deal, reproducible provenance, missing data versus business facts.

**Acceptance evidence:**

- [ ] Valid reference CSV yields the intended records, date types and exact pence.
- [ ] Bad inputs are rejected with useful errors and no silently dropped rows.
- [ ] Leading zeros and literal NA survive ingestion.
- [ ] Synthetic sample and small invalid fixtures are documented; relevant loader/validation tests actually pass.

**Out of scope:** No arbitrary column mapper, Excel imports, CRM sync, UI or forecasting implementation.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Have me inspect a tiny CSV as raw text and predict which values would be misread by automatic type inference.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 03 — pandas Pipeline, Conversion and Sales-Cycle Metrics

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 03 — pandas Pipeline, Conversion and Sales-Cycle Metrics**, milestone **1 — Trustworthy data and baseline metrics**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Implement independently testable current-pipeline, outcome and cycle metrics from validated data.

**Prerequisites:** Phase 02 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Learn boolean masks, filtering, groupby, aggregation and stable stage ordering through one metric at a time.
2. Implement current open count/amount and stage count/amount totals.
3. Implement period closed win rate with numerator/denominator and observed creation-cohort conversion with open-cohort count.
4. Calculate won-deal cycle days and median using actual-close period selection.
5. Apply owner filtering consistently; handle empty denominators as N/A; verify source frames are not mutated and reconcile independent goldens.

**Technical concepts:** DataFrame masks, grouping, sums/counts, date subtraction, median, function contracts, unit tests.

**Commercial concepts:** win rate versus cohort conversion, denominator choice, maturity bias, current pipeline versus period outcomes.

**Acceptance evidence:**

- [ ] Core reference metrics reconcile to the exact expected rows and values.
- [ ] No closed outcomes / no created cohort / no wins produce the required N/A results.
- [ ] Owner-filter results and stage totals reconcile.
- [ ] Metrics run without Streamlit, file access or a network and relevant tests pass.

**Out of scope:** No risk flags, forecasting, plotting-heavy work or new architecture layers.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Have me write the row-selection rule for the closed win-rate denominator before translating it into a pandas mask.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 04 — Stalled Deals, Timing and Commercial Risk

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 04 — Stalled Deals, Timing and Commercial Risk**, milestone **2 — Commercial decision engine and dashboard**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Create transparent risk flags that a sales manager can inspect and act on without confusing heuristics with facts.

**Prerequisites:** Phase 03 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Implement stage age, inactivity, overdue, missing-activity and stalled flags using the exact thresholds and declared snapshot date.
2. Test equality boundaries and missing values; explain why no activity date is not the same as zero activity.
3. Aggregate stalled / overdue / missing categories and the unique at-risk union without double counting.
4. Trace D002, D003 and D004 through the flags and explain a useful owner follow-up for each.
5. Keep risks separate from probabilities; do not automatically rewrite dates, weights or outcomes.

**Technical concepts:** date arithmetic, boolean OR, null semantics, set unions, derived columns, boundary testing.

**Commercial concepts:** deal hygiene, stalled opportunities, overdue timing, review heuristics and actionability.

**Acceptance evidence:**

- [ ] Reference stalled and at-risk unions each equal 3 deals / £90k; overdue equals £40k.
- [ ] 14/30-day equality boundaries and due-today rules are tested.
- [ ] Missing activity is visible and not misrepresented as measured inactivity.
- [ ] I can trace flags to rows and explain overlap.

**Out of scope:** No ML risk score, automatic probability reduction, auto-requalification or alerting system.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Ask me to calculate D003 stage age and explain why a deal can be flagged while still remaining in a forecast.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 05 — Forecasting, Money and Pipeline Coverage

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 05 — Forecasting, Money and Pipeline Coverage**, milestone **2 — Commercial decision engine and dashboard**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Build a deterministic, auditable period bookings forecast and correctly scoped remaining-target coverage.

**Prerequisites:** Phase 04 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Translate eligibility into masks; exclude overdue/out-of-period open deals while retaining them in current pipeline.
2. Use integer pence and Decimal probabilities with half-up rounding for each deal; sum deal weights.
3. Calculate actual won + weighted eligible open = period forecast, remaining target, coverage and forecast gap.
4. Check the £53.5k forecast and 0.75× coverage by hand; implement target-met and empty cases.
5. Exercise the two 5p deals precision oracle and a probability change; explain assumptions and bookings versus accounting revenue.

**Technical concepts:** Decimal, integer money, rounding rules, deterministic functions, selection boundaries, ratios and tests.

**Commercial concepts:** weighted forecasts, target gap, coverage numerator/denominator, probability assumptions and forecast limitations.

**Acceptance evidence:**

- [ ] Reference forecast bridge is £20k + £33.5k = £53.5k; remaining target £80k; coverage 0.75×.
- [ ] Two 5p qualification deals produce £0.02 weighted total under the contract.
- [ ] Target met yields N/A coverage, with an explanatory label.
- [ ] Due-today, period-end, owner and 0/1 probability cases pass; I can defend the eligibility and rounding rules.

**Out of scope:** No accounting-recognition engine, advanced scenarios, ML calibration or universal coverage benchmark.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Have me select eligible reference deals on paper before we implement the timing mask.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 06 — Streamlit Dashboard and Useful User Flow

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 06 — Streamlit Dashboard and Useful User Flow**, milestone **2 — Commercial decision engine and dashboard**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Make the tested calculations useful through a small complete local user workflow.

**Prerequisites:** Phase 05 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Introduce Streamlit execution/reruns, widgets and session state through the sample-data flow.
2. Wire sample data and uploads to the same validation/calculation path; keep formulas out of the UI file.
3. Build the overview, deal-review and forecast views with built-in cards, charts and tables.
4. Show date/scope, numerator/denominator and assumptions; require target reconfirmation when owner scope changes.
5. Exercise invalid upload after valid upload, empty selection, missing data and sample reset; clear stale output and keep uploads in session memory.

**Technical concepts:** UI versus calculation boundaries, reruns, state, controls, formatting, data tables, manual workflow checks.

**Commercial concepts:** decision-focused presentation, source-row drilldown, clear definitions, target ownership.

**Acceptance evidence:**

- [ ] A local app completes bundled-data and valid-upload workflows.
- [ ] Displayed reference metrics reconcile to pure-function outputs.
- [ ] Invalid or empty states never show misleading stale KPIs.
- [ ] Owner/target interaction works, forecast weights and caveats are visible, and the learner can trace a displayed result.

**Out of scope:** No custom React frontend, elaborate styling, accounts, database or extra charting framework without a concrete need.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Guide me to display one already-tested metric from the bundled data, then add one useful control.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 07 — HTTP, JSON and API Fundamentals

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 07 — HTTP, JSON and API Fundamentals**, milestone **3 — HTTP fundamentals and shipped application**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Understand request/response transport and data contracts through a small local read-only exercise.

**Prerequisites:** Phase 06 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Create a small synthetic JSON records fixture equivalent to a known CSV fixture.
2. Serve only examples/api on localhost using Python http.server; explain method, host, port and path.
3. Fetch with urllib.request and an explicit timeout; inspect status, response headers and decoded JSON.
4. Observe and handle a missing-path 404; compare HTTP failure with a 200 response whose data fails business validation.
5. Use the shared validation and calculation semantics on decoded records; compare results to CSV and stop the server. Explain future authentication/pagination/rate-limit requirements without implementing them.

**Technical concepts:** HTTP GET, URLs, status codes, headers, JSON, timeout/error handling, transport versus schema validation.

**Commercial concepts:** CRM export versus integration, consistent snapshots, trustworthy inputs across transports.

**Acceptance evidence:**

- [ ] A real local GET response and 404 are observed and recorded.
- [ ] Equivalent JSON/CSV records yield the same validated calculation results.
- [ ] I can explain the transport/validation boundary and what a real CRM connector would still need.
- [ ] The exercise is local and optional at runtime; the dashboard works without it.

**Out of scope:** No public HTTP server, full REST backend, OAuth, real CRM requests, production integration or new application service.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Ask me to trace what happens between requesting a local JSON URL and obtaining a Python records list.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 08 — Reliability, Clean Setup and Deployment

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 08 — Reliability, Clean Setup and Deployment**, milestone **3 — HTTP fundamentals and shipped application**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Demonstrate reproducible correctness and a working live synthetic-data dashboard at a recorded commit.

**Prerequisites:** Phase 07 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Review existing tests against the specification; fill meaningful gaps in invalid inputs, thresholds, filters, precision and end-to-end CSV handling.
2. Record exact tested dependencies; install and run from a fresh environment; avoid new infrastructure unrelated to delivery.
3. Measure a 10,000-row validation/calculation run and record actual timing/hardware; fix a genuine bottleneck only if needed.
4. Check current official hosting instructions, publish the synthetic-data repository when appropriate and deploy the Streamlit entry point.
5. Verify the live sample route and synthetic upload in a fresh session; inspect errors/state, document the URL, commit, commands, results and material limitations.

**Technical concepts:** regression/integration tests, dependency reproducibility, logs, deployment configuration, build versus runtime failures.

**Commercial concepts:** trust, repeatable demonstrations and distinguishing evidence from claims.

**Acceptance evidence:**

- [ ] Relevant tests actually pass with output recorded at a known commit.
- [ ] A clean setup installs and launches using the documented commands.
- [ ] A live URL is reachable and the complete synthetic-data flow is observed.
- [ ] Uploads are not intentionally persisted or shared-cached; no client data/secrets are published; performance observations are factual.

**Out of scope:** No paid hosting purchase, Kubernetes, production authentication, arbitrary test-coverage target or browser-test framework.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Help me compare the current verification evidence with the acceptance checklist and identify the single most consequential gap.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Phase 09 — Sales Insights, Portfolio Story and Independent Mastery

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 09 — Sales Insights, Portfolio Story and Independent Mastery**, milestone **4 — Portfolio and independent mastery**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Turn the completed application into defensible portfolio evidence and demonstrate independent technical/commercial understanding.

**Prerequisites:** Phase 08 is COMPLETE with observed evidence and an updated handoff.

**Guide these activities one meaningful step at a time:**

1. Produce exactly three insights from the finished synthetic dashboard: finding, source-row evidence, implication, action and caveat.
2. Write a concise README/case study with live URL, screenshots, setup/tests, data contract, architecture, decisions and limitations.
3. Prepare a 3–5 minute demo that traces one record and explains the forecast bridge and risk flags.
4. Have me independently change a small rule/probability, predict the effect and verify it; inject or diagnose one realistic bug.
5. Review all final gates and update the final PROJECT_STATE with actual evidence and honest uncompleted items.

**Technical concepts:** system tracing, change impact, debugging, explaining trade-offs, reproducible demonstration.

**Commercial concepts:** turning descriptive metrics into actions without causal overclaiming or false forecast confidence.

**Acceptance evidence:**

- [ ] A concise portfolio story links to the live dashboard, sample data and actual validation evidence.
- [ ] Three sales insights are specific, actionable and defensible.
- [ ] I can trace, modify and debug the core flow and explain its limitations.
- [ ] Final status is COMPLETE only if every required delivery gate is evidenced.

**Out of scope:** No invented business impact, production users, CRM integration, predictive AI or extra features to improve the story.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Ask me to explain the application to a sales manager in 60 seconds, then review the evidence for my first insight.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.


---

# Resume the Current Phase

Resume my Sales Pipeline Intelligence Tool apprenticeship. Read the latest `docs/PROJECT_STATE.md`, the current phase prompt, engineering specification, tutor protocol and relevant changed files/output.

Identify what is implemented and verified, what is only planned, the exact point we stopped and any unresolved issue. Do not restart completed work or infer test passes from a summary. If you lack access, request the smallest necessary file/output.

Explain the next concept and guide one meaningful action. Preserve the current phase gate; do not advance until behaviour and understanding are evidenced.


---

# End-of-Phase Review

Review the current Sales Pipeline Intelligence Tool phase against its actual acceptance criteria.

1. Inspect observed inputs/outputs, relevant test results and changed files. State what was not run or cannot be verified.
2. Reconcile at least one meaningful result to independent expectations / source rows.
3. Ask 3–5 targeted understanding questions and let me answer before scoring understanding.
4. Return COMPLETE or NOT YET COMPLETE with specific remaining gaps. Passing functionality without understanding does not complete the apprenticeship gate.
5. Update `docs/PROJECT_STATE.md` with working behaviour, changed files, decisions, commands/results, learning gaps, blockers and the exact next action.
6. Have me review the diff and commit the meaningful work/handoff. Never invent a commit, push or live deployment.
