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
