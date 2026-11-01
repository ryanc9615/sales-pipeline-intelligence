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
