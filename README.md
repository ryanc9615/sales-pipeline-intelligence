# Sales Pipeline Intelligence Tool

A guided portfolio project: upload a synthetic CRM CSV and turn it into trustworthy pipeline, conversion, risk and bookings-forecast decisions.

**Current status:** Planning prepared; implementation NOT STARTED.  
**Timebox:** Three-week target, approximately 40 focused hours (36–48 planning range).  
**Stack:** Python + pandas + Streamlit + pytest + Git.  
**Coaching:** ChatGPT acts as tutor, CTO, architect, senior engineer and commercial reviewer while Ryan builds and learns.

## What V1 will do

- Validate one canonical CSV snapshot for one fictional GBP business.
- Show current open pipeline, stage amounts/counts, closed win rate, observed creation-cohort conversion and median won-deal cycle.
- Flag stalled, overdue and missing-activity deals without double counting.
- Calculate an explainable weighted **bookings / contract-value forecast** and coverage of the remaining period target.
- Provide a deployed synthetic-data dashboard and three actionable sales insights.

The forecast does not implement accounting revenue recognition. Stage probabilities are explicit assumptions. A current-state snapshot cannot reconstruct stage history or prove stage-to-stage conversion.

## Start here

1. Read this page and `docs/PHASE_ROADMAP.md`.
2. Use `docs/TUTOR_PROTOCOL.md` as the ChatGPT Project coaching instructions; see `docs/GITHUB_SETUP.md` for setup details.
3. Keep `docs/ENGINEERING_SPEC.md` and `docs/CALCULATION_EXAMPLES.md` as the scope/calculation contract.
4. Start a guided conversation with `prompts/phase_00.md` and the latest `docs/PROJECT_STATE.md`.
5. Build one step at a time. Close each phase with observed evidence, an understanding check and an updated handoff.

## Project documents

| File | Purpose |
|---|---|
| [Original scope](ORIGINAL_SCOPE.md) | User brief and explicit planning assumptions |
| [Engineering specification](ENGINEERING_SPEC.md) | CSV contract, formulas, constraints, architecture and acceptance |
| [Phase roadmap](PHASE_ROADMAP.md) | Three-week schedule and ten phase gates |
| [Tutor protocol](TUTOR_PROTOCOL.md) | Copy-ready coaching instructions |
| [Phase prompts](PHASE_PROMPTS.md) | One conversation starter per phase, plus resume/review prompts |
| [Project state](PROJECT_STATE.md) | Current progress, factual verification and exact next action |
| [Calculation examples](CALCULATION_EXAMPLES.md) | Hand-derived oracle for correctness |
| [Decisions](DECISIONS.md) | Trade-offs, scope changes and parked ideas |
| [Setup and GitHub workflow](GITHUB_SETUP.md) | Local, Git and ChatGPT reference setup |
| [Portfolio evidence](PORTFOLIO_EVIDENCE.md) | Live-demo, test and three-insight completion evidence |

## Same structure as Scenario Financial Engine

This pack follows the same `docs/` + `prompts/` model, source hierarchy, phased tutor conversations, acceptance gates and project-state handoffs. It also provides a starter archive and a reference-materials archive. The backend/database work of that project is replaced with the narrower CSV → pandas → Streamlit workflow appropriate here.

The starter intentionally contains no implemented application or pre-existing Git history. Do not mistake empty planned folders or these documents for working features.

## Definition of done

A live, usable dashboard; canonical synthetic sample data; relevant tests actually passing against independent expected values; a reproducible setup; observed API/HTTP learning evidence; three commercially useful insights; and the ability to explain, modify and debug the core flow independently. See the specification and portfolio checklist for the exact gates.

**First action:** Open `prompts/phase_00.md` and inspect your actual local environment with the tutor. Do not start by installing every package or generating the entire app.
