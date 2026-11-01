Sales Pipeline Intelligence Tool — Project State
Updated 1 November 2026 from the Phase 00 handoff, Phase 01 tutoring conversation, and supplied project references. This is a replacement file for the learner to review in their local repository. It has not been synchronised, committed, pushed, or executed on the learner's Mac. Actual repository files and test outputs remain the implementation authority.

Current position
- Milestone: 1 — Trustworthy data and baseline metrics.
- Phase 01 working session: CLOSED at learner request on 1 November 2026.
- Formal Phase 01 gate: NOT YET COMPLETE — learning evidence outstanding. Closing the session does not certify that all acceptance criteria were demonstrated. Do not report Phase 01 as an independently passed gate.
- Last formally accepted phase: 00 — Setup and Development Workflow (COMPLETE according to the supplied Phase 00 handoff).
- Next intended working phase: 02 — CSV Ingestion, Validation and Sample Data, after the short outstanding Phase 01 evidence check. The user requested to move on rather than continue lengthy theory exercises.
- Git continuity: First local commit bc068ae was verified in Phase 00. A later Phase 00 handoff commit, current branch status, and any later commits have not been observed.
Working functionality and observations
- Previously observed in Phase 00: python -m app printed Sales Pipeline Intelligence Tool: environment ready. The committed app/__main__.py code was inspected and matched that smoke output.
- Phase 01 output: commercial/data-contract explanations, worked-through examples, and learner discussion, all within the tutoring conversation. No Phase 01 application functionality was implemented or tested in the supplied evidence.
- Not implemented or verified: CSV loading/validation, canonical pandas data, metric functions, risk flags, bookings forecasts, Streamlit interface, HTTP exercise, automated application tests, live deployment.
- Local repository access: The learner's Mac working tree and latest docs/PROJECT_STATE.md were not accessible here. No claim is made that any local repo file has changed.
Files reviewed and changed
Read as evidence: docs/ORIGINAL_SCOPE.md, docs/ENGINEERING_SPEC.md, docs/CALCULATION_EXAMPLES.md, docs/PHASE_ROADMAP.md, docs/TUTOR_PROTOCOL.md, docs/DECISIONS.md, Phase 01 prompt in docs/PHASE_PROMPTS.md, and the most recent supplied Phase 00 handoff PROJECT_STATE_phase00_complete (1).md.

Prepared in assistant workspace for replacement: docs/PROJECT_STATE.md (this handoff).

No changes required to: docs/ENGINEERING_SPEC.md, docs/DECISIONS.md, docs/PHASE_ROADMAP.md, or the independent calculation examples. No new business rule or acceptance criterion was agreed. In particular, the contract still allows expected_close_date to be blank on closed deals; historical forecast accuracy and stage progression remain deferred.
Phase 01 commercial and data semantics (contract reviewed; not implemented)
- Business basis: One fictional business, one present-state CRM CSV, one row per opportunity, GBP total contract value. A won contract contributes to bookings, not necessarily recognised revenue or cash.
- Reference controls: CSV snapshot 2026-10-31; current reporting period 2026-10-01 to 2026-12-31 inclusive; all owners; period bookings target £100,000.
- Required CSV headers (11): deal_id, deal_name, owner, stage, amount, currency, created_date, expected_close_date, actual_close_date, stage_entered_date, last_activity_date. Headers are required even where cells may be empty.
- Open stages: qualification, discovery, proposal, negotiation. Closed stages: closed_won, closed_lost. Open/closed status is derived from stage; expected-close timing does not determine status.
- Open opportunity dates: created_date, expected_close_date and stage_entered_date required; actual_close_date must be empty; last_activity_date optional.
- Closed opportunity dates: created_date and actual_close_date required; expected_close_date, stage_entered_date and last_activity_date optional. Supplied optional dates must satisfy the specification's ordering rules.
- Date ordering: created_date ≤ snapshot; supplied expected_close_date ≥ creation; closed actual close between creation and snapshot; open stage-entry between creation and snapshot; closed supplied stage-entry ≤ actual close (and ≥ creation); supplied activity between creation and snapshot. ISO YYYY-MM-DD only.
- Money and identifiers: Read source cells as strings; preserve 0007 and literal NA as identifiers/text, strip surrounding whitespace, normalise stage case and currency case only as specified. Parse amounts via Decimal from original strings, then canonical integer pence; at most two decimal places. Preserve missing dates as missing, not zeros or invented dates.
- Hard validation: Reject the complete invalid dataset with actionable errors; do not silently truncate 15000.005, discard records, deduplicate, or replace missing business information. For valid rows, no hidden use of today's date in calculations.
- Forecast probabilities: 10%, 25%, 50%, 75% for the four open stages; 100% won, 0% lost. These are assumptions, not learned win rates. Forecast calculations use Decimal and per-deal ROUND_HALF_UP to whole pence.
Independently supplied reference oracle — not learner or code verification
The following values were defined in docs/CALCULATION_EXAMPLES.md and reconciled during tutoring. They are not results from executed software or a fully independent learner derivation.
Metric	Contributing rows and arithmetic	Expected result
Current open pipeline	D001 £10k + D002 £20k + D003 £30k + D004 £40k + D008 £10k	£110,000, 5 open
Period closed win rate	D005 and D007 won; D006 lost, all actually closed in Q4	2/3 = 66.7%
Observed creation-cohort conversion	D007 currently won / (D007 won + D008 open), both created in Q4	1/2 = 50%, 1 open
Median won-deal cycle	D005: 1 Sep → 20 Oct = 49 days; D007: 1 Oct → 11 Oct = 10 days	(49 + 10)/2 = 29.5 days


Current pipeline includes overdue D004 and out-of-period D008 because both are open at the snapshot. Period-eligible open pipeline excludes them: D001 + D002 + D003 = £60k; weighted eligible open £33.5k; actual Q4 won £20k; total period bookings forecast £53.5k. Later forecasting implementation must use actual per-deal rounding and correct eligibility.
Learner understanding actually observed
Demonstrated:
- Differentiated anticipated closing from confirmed won/closed outcomes and correctly classified D004 as open, D005 as closed, with D004 contributing to open pipeline.
- Challenged the optional expected-close date on closed deals for useful commercial reasons (forecast versus actual, resourcing); recognised the need for historical exports or stage-change records to know previous stages.
- Identified why leading-zero IDs should stay strings for exact matching; recognised integer money as appropriate.
- After discussion of materiality versus data integrity, chose source-owner correction and re-upload rather than silent truncation of a three-decimal amount.
Corrections taught during Phase 01 (not independently re-tested):
- created_date is opportunity-record creation, not necessarily first lead conversation.
- Blank actual_close_date means the opportunity is open, not merely that expected close has not yet passed.
- stage_entered_date is required for open deals; expected_close_date is optional for closed deals.
- A £15k contract won in October for equally delivered November–January services gives £15k October bookings but £0 October recognised revenue under the example's assumption.
- float is generally unsuitable for exact financial cents/pence because binary fractions can produce rounding artefacts; money uses original-string Decimal and integer pence.
Still missing for Phase 01 gate: independent complete explanation of 11-field/conditional-date contract; learner-derived D001–D008 reference arithmetic for all four values; concise explanation of amount/snapshot/architecture controls without relying exclusively on given answer text. The formal end-of-phase five-question review was proposed but not answered; the learner then asked to close the phase.
Decisions, scope control and learning/portfolio evidence
- No contract change accepted. Keep docs/DECISIONS.md unchanged. Historical forecast snapshots, stage-transition logs and operational capacity planning are worthwhile PARK FOR LATER topics, not V1 requirements.
- Data-quality evidence: The learner initially argued half-penny truncation was immaterial, then chose strict schema validation and source-owner correction. Preserve this as the reasoning example; do not claim a validator or audit log has been implemented.
- Architecture trade-off: Current snapshot only (simple CSV → validation → canonical pandas DataFrame → pure calculations → Streamlit UI) versus event history (required for past-stage or historical forecast accuracy); keep single-snapshot V1.
- Future evidence still needed: a calculation correction demonstrated independently, a reproduced bug diagnosis, observable commands/tests, and a deployed synthetic demo.
Verification / blockers
- Phase 01 commands and automated tests observed: none. This was a commercial/data-design discussion, not an implementation phase.
- Existing smoke and Git evidence: Phase 00 only; first commit bc068ae historical, not assumed current.
- Working tree, new commit hash, GitHub remote, live URL: not observed or verified.
- Formal blocker: Phase 01's understanding/independent-calculation gate remains open. This is a documentation/evidence gap, not an identified software defect.
Exact next action and Git handoff
1. Review and replace the local docs/PROJECT_STATE.md with this file; ensure it doesn't overwrite a newer local handoff. Retain the supplied engineering spec and independent calculation examples unchanged.
2. From the local project root, inspect the change: git status --short --branch and git diff -- docs/PROJECT_STATE.md.
3. Stage only the intended handoff: git add docs/PROJECT_STATE.md; check git diff --cached --check and git diff --cached -- docs/PROJECT_STATE.md; commit, for example git commit -m "docs: close Phase 01 session and record acceptance gaps".
4. Verify git log -1 --oneline and git status --short --branch; report observed results at next check-in. Do not claim a commit until verified.
5. Before declaring Phase 01 COMPLETE / treating milestone gate as passed: do a compact learner-led check of (a) open vs closed conditional date rules and (b) four independent deal-level sums, ratios and cycle days; assess and record actual answers. This can be done at the start of the next session rather than repeating the full theory lesson.
6. Then start Phase 02: inspect a tiny raw CSV, predict where automatic type inference would corrupt leading-zero IDs, literal NA or amounts, and implement loading/validation one small increment at a time. No dashboard or forecast code yet.
Phase 00 historical handoff (for continuity)
- Observed environment: macOS, /bin/zsh, Python 3.12.5, project-specific .venv; project path ~/Documents/Projects/LearningAI/sales-pipeline-intelligence.
- First observed local commit bc068ae (chore: establish Python project and development workflow); clean tree verified at that point only.
- app/__init__.py package marker and app/__main__.py smoke entry point observed; no external dependencies or analytics tests then.
- Phase 00 documentation follow-up commit and subsequent local changes remain unverified.