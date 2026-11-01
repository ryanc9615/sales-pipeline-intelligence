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
