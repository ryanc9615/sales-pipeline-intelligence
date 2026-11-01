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
