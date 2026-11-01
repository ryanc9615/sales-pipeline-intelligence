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
