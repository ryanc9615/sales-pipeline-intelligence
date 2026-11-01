# Phased Build Roadmap — Sales Pipeline Intelligence Tool

**Status:** Planning prepared; application implementation NOT STARTED.  
**Format:** Four delivery milestones, ten guided phases / conversations (00–09). A phase may take more than one session. Advance on evidence and understanding, not calendar dates.

| Milestone | Phases | Delivery gate |
|---|---|---|
| 1 — Trustworthy data and baseline metrics | 00–03 | Validated synthetic CSV → independently checked pipeline / conversion / cycle metrics, without a UI |
| 2 — Commercial decision engine and dashboard | 04–06 | Risks, forecasting and coverage reconcile; a usable local Streamlit workflow |
| 3 — HTTP fundamentals and shipped application | 07–08 | Observed HTTP exercise, clean setup, tests and a live synthetic-data dashboard |
| 4 — Portfolio and independent mastery | 09 | Three defensible sales insights, demo evidence and a learner-led change/debug exercise |

## Three-week working plan

| Week | Target phases | Focused effort baseline | What should exist by the end |
|---|---|---:|---|
| 1 | 00–03 | 15 hours | Reproducible environment, agreed data contract, sample fixtures, validation and core metrics |
| 2 | 04–06 | 15 hours | Deal risks, weighted bookings forecast, remaining-target coverage and a complete local dashboard |
| 3 | 07–09 | 10 hours | HTTP learning evidence, clean-install checks, deployed demo, README, three insights and technical mastery review |

Baseline total: **40 hours**; planning range **36–48**. Protect contingency for deployment and debugging. Calendar weeks are relative to the learner's actual start. If only 6 hours/week are available, extend the calendar; do not compress understanding or remove calculation checks.

## Ordered phases

| Phase | Conversation | Baseline hours | Tangible result / gate |
|---|---|---:|---|
| 00 | Setup and development workflow | 2 | Interpreter/venv understood; tiny package entry point runs; first meaningful local Git commit |
| 01 | Sales domain, data contract and manual examples | 3 | Explain stage/status/amount/date semantics; derive reference calculations; agree the canonical schema |
| 02 | CSV ingestion, validation and sample data | 5 | Raw CSV → validated canonical data or useful errors; deterministic synthetic demo and small fixtures |
| 03 | pandas pipeline, conversion and sales-cycle metrics | 5 | Tested core metrics match independent expectations and use correct denominators |
| 04 | Stalled deals, timing and commercial risk | 4 | Explainable deal-level flags; tested thresholds; risk union does not double count |
| 05 | Forecasting, money and pipeline coverage | 5 | Period forecast bridge and remaining-target coverage reconcile exactly |
| 06 | Streamlit dashboard and useful user flow | 6 | Complete local sample/upload flow, controls, charts, tables and clear invalid/empty states |
| 07 | HTTP, JSON and API fundamentals | 2 | Local read-only GET exercise; observed 200/404; same validation/calculation contract for a small records fixture |
| 08 | Reliability, clean setup and deployment | 5 | Relevant tests pass, clean environment works and live synthetic demo is checked at a recorded commit |
| 09 | Sales insights, portfolio story and mastery | 3 | Three actionable insights, concise demo, documented limitations and an independently completed rule change / bug diagnosis |

Dependencies are sequential. Keep calculation checks next to each feature; Phase 08 is a final reliability review, not the first time testing begins.

## Repeatable conversation protocol

1. Open the next conversation in the same ChatGPT Project and use that phase's prompt from `prompts/` or `docs/PHASE_PROMPTS.md`.
2. Supply the current repository `docs/PROJECT_STATE.md` and specific files/output if the tutor cannot access them.
3. Build one meaningful increment, run it, inspect it and explain it. Keep a useful commit history.
4. Close with `prompts/_end_phase_review.md`. A phase is COMPLETE only with behaviour evidence **and** understanding.
5. Update the handoff, review the diff and commit it. Resume with `_resume_phase.md` if a chat ends mid-phase.

## Scope/time control

At the end of Weeks 1 and 2, compare actual effort and the remaining mandatory gates. If behind, simplify chart styling, avoid extra filters and use a concise README rather than an elaborate portfolio site. Keep the sample upload, required metrics, validation, independent tests and deployed dashboard.

A new feature must either replace work of comparable size without compromising the required outcome, or be explicitly deferred. Do not quietly add integrations, AI, a database or advanced frontend work.

## Evidence needed to advance

- Working input/output for the phase and relevant failure examples.
- Actual commands and observed test output; no invented passes.
- The learner can explain the important mechanics and at least one trade-off.
- Current project state with concrete evidence and the next action.
- Changes reviewed and recorded in Git when a repository exists.
