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
