# Portfolio Evidence — Sales Pipeline Intelligence Tool

**Status:** Checklist and templates only; no application completion evidence has been collected yet.

## Required deliverables

| Evidence | What counts as complete | Record |
|---|---|---|
| Live dashboard | Reachable URL; fresh-session sample flow and synthetic upload both work | URL, date and deployed commit: pending |
| Sample dataset | Deterministic fictional CRM CSV, approximately 100–200 rows; declared snapshot, dates and amount basis; varied owners/stages/outcomes/risks | Filename / generation method: pending |
| Validated calculations | Golden-case expectations, edge tests and actual pytest output | Command / result / commit: pending |
| Data quality | Show a useful rejection and explain why silent correction would mislead | Example / screenshot: pending |
| Three sales insights | Each grounded in current dashboard rows and tied to a specific action | See template below |
| Technical explanation | Trace bytes → validation → DataFrame → metric → UI; explain money, dates, denominators and assumptions | README section / demo: pending |
| API fundamentals | Observed local GET/JSON/200/404 and contract validation; label scope accurately | Exercise note: pending |
| Reproducible setup | Another clean environment installs, tests and launches at a recorded commit | Versions / commands / result: pending |
| Independent skill | Learner changes a rule, predicts the effect and fixes one injected bug | Short learning note: pending |

## Suggested 3–5 minute demo

1. State the sales manager's problem and choose the synthetic sample.
2. Explain the snapshot date and show one validation failure, then recover with a valid file.
3. Trace a KPI to its deals and demonstrate the owner filter / target scope.
4. Explain the forecast bridge and one risk flag, including a limitation.
5. State the three actions, show validation/test evidence and identify the next useful enhancement.

## Insight template — repeat exactly three times

- **Finding:** A precise number, denominator, period and owner scope.
- **Evidence:** The metric and deal IDs / source rows supporting it.
- **Commercial implication:** Why a sales manager should care.
- **Proposed action:** A specific next step and responsible role, without implying contact was made.
- **Caveat / follow-up:** What the data cannot establish and what would confirm the interpretation.

Avoid claiming causation, using unsupported “industry standard” coverage ratios or declaring a deal lost from a heuristic alone.

## README / case-study outline

Problem and intended user; live demo and synthetic-data note; 2–3 screenshots; one-paragraph architecture; setup/test/launch commands; CSV contract; metric definitions; independently validated example; three insights; trade-offs and limitations; planned next step.

Only record screenshots and results after running the app. Do not replace evidence with a generated mockup. Keep uploaded client data and personal information out of screenshots and the repository.

## Honest CV / portfolio wording after completion

“Built and deployed a Python/pandas/Streamlit sales pipeline dashboard that validates CRM CSV exports, identifies stalled and overdue opportunities, and calculates explainable weighted bookings forecasts and target coverage. Tested calculations against independent reference cases and translated outputs into three sales actions.”

Use this only after those actions have happened. Do not claim a live CRM integration, predictive ML, production users, measured revenue improvement or a REST backend unless separately implemented and evidenced.
