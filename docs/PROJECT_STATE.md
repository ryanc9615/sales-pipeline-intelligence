Sales Pipeline Intelligence Tool — Project State
Keep this factual and update it at the end of each working phase. Planning documents are not proof of implementation. The current repository copy takes precedence over an old uploaded snapshot.

Current position
- Phase: 00 — Setup and Development Workflow
- Status: COMPLETE — technical and learning acceptance verified. Final documentation-only follow-up commit for this handoff is still pending; do not claim it exists until checked.
- Last completed phase: 00 — Setup and Development Workflow
- State updated: 1 November 2026, using learner-supplied terminal output and the Phase 00 understanding review
- Current milestone: 1 — Trustworthy data and baseline metrics (in progress; Phase 01 next)
Working functionality
- The starter planning and tutoring pack exists locally, including scope, engineering specification, roadmap, manual calculation examples and phase prompts.
- A minimal Python package exists with an empty app/__init__.py and an executable app/__main__.py.
- Observed after the first commit: python -m app printed exactly Sales Pipeline Intelligence Tool: environment ready.
- Observed committed source: git show HEAD:app/__main__.py displayed a main() function printing that message, guarded by if __name__ == "__main__": main(). The source matches the observed smoke-test behaviour.
- No CSV loader, validation, pandas calculations, forecasting, Streamlit UI, HTTP exercise, third-party runtime dependencies or automated application tests have been implemented or verified.
- No remote GitHub repository or live deployment has been evidenced.
Repository / important files
- app/__init__.py: observed empty package marker.
- app/__main__.py: minimal smoke entry point, verified both by execution and from the committed source.
- .gitignore: inspected; excludes .venv/, __pycache__/, Python/test artefacts and common local secrets.
- README.md: project overview and setup order.
- docs/ORIGINAL_SCOPE.md: original user brief and planning assumptions.
- docs/ENGINEERING_SPEC.md: V1 input, calculation, UI and delivery contract.
- docs/PHASE_ROADMAP.md: phases, hours and acceptance gates.
- docs/TUTOR_PROTOCOL.md: ChatGPT coaching instructions.
- docs/PHASE_PROMPTS.md and prompts/phase_00.md through phase_09.md: guided conversation starters.
- docs/CALCULATION_EXAMPLES.md: independent reference values, including precision and boundary cases.
- docs/DECISIONS.md: baseline choices and parked ideas.
- docs/PORTFOLIO_EVIDENCE.md: portfolio evidence checklist and insight template.
- docs/GITHUB_SETUP.md: local setup, publication and reference instructions.
- data/README.md and tests/README.md: planned work only, not runtime data or passing tests.
- docs/PROJECT_STATE.md: this handoff; its final updated contents still require a local Git commit.
Decisions / architecture
- Python + pandas + Streamlit remain the planned V1 stack; pandas and Streamlit are not yet installed in the project environment.
- A project-specific .venv is used for isolation. No third-party packages have been added in Phase 00.
- Retain a minimal python -m app smoke entry point because reproducible execution is useful even before analytics exist.
- Original calculation contract is unchanged: one GBP CSV snapshot, integer pence, Decimal probabilities, per-deal half-up rounding, and explicit snapshot/reporting dates.
- Current open pipeline remains distinct from period-eligible pipeline; win rate and observed creation-cohort conversion must not be confused with historical stage transitions.
- Local HTTP exercise is future learning work; no live CRM integration or separate backend.
- No scope-changing decision has been made. See docs/DECISIONS.md.
Verification
- Operating system / shell: macOS (Darwin), /bin/zsh, verified using uname -s and echo "$SHELL".
- Local project directory: ~/Documents/Projects/LearningAI/sales-pipeline-intelligence (observed pwd).
- Base Python: Python 3.12.5; command -v python3 resolved to /Library/Frameworks/Python.framework/Versions/3.12/bin/python3.
- Virtual environment: created with python3 -m venv .venv; activated in zsh. command -v python and sys.executable resolved inside the project's .venv/bin/; sys.prefix was the project .venv; sys.base_prefix was /Library/Frameworks/Python.framework/Versions/3.12.
- Smoke run after commit: python -m app -> Sales Pipeline Intelligence Tool: environment ready (observed in supplied terminal output, 1 November 2026).
- Committed executable source: git show HEAD:app/__main__.py showed def main(): print(...) and the __name__ == "__main__" guard (observed; source matches smoke output).
- Git version: 2.39.3 (Apple Git-146).
- Git init: git init -b main succeeded; initial git status showed an empty repository with untracked starter files.
- Git ignore evidence: git check-ignore -v identified .gitignore line 2 for .venv/ and line 5 for app/__pycache__/.
- Staging evidence: explicit paths were staged; git status --short showed additions and git diff --cached --stat was inspected. The original staged app/__main__.py was empty, prompting a correction. The user subsequently made a successful first commit; a final full staged patch review was not separately pasted in chat.
- First local commit: bc068ae (chore: establish Python project and development workflow), verified with git log -1 --oneline.
- Clean working tree at that commit: git status --short --branch returned ## main without other entries. Recheck after editing this handoff.
- Automated application tests observed passing: None; none implemented. The package smoke test is not an analytics calculation test.
- Live URL: None; not deployed.
- Editor: Not positively identified from supplied output.
Learning outcomes
- Explained and demonstrated: terminal working directory; OS and shell; base versus active virtual-environment interpreter; package entry point; installed Git versus an initialised repository; ignore rules; untracked, staged and committed file states; local commit versus a remote push.
- Learner explained why package isolation avoids dependency-version conflicts and why .venv is excluded from Git.
- Learner correctly explained that a commit includes the staged version, not later unstaged edits (after an earlier corrected misconception).
- Learner identified that python -m app proves entry-point execution; tutor reinforced that a successful smoke test does not validate sales metrics or business correctness. Revisit this distinction when writing independent golden-value tests.
- Four targeted Phase 00 understanding questions were answered and reviewed; technical and conceptual gate is accepted.
- Still to practise: reviewing a complete staged patch before a documentation commit; dependency declarations when dependencies are actually introduced.
Known issues / blockers
- No identified technical blocker to Phase 01.
- Documentation follow-up pending: this revised docs/PROJECT_STATE.md has not yet been observed committed on the Mac. Do not invent a follow-up commit hash or claim a clean post-update tree.
- Project reference-file replacement and local Mac file replacement are separate manual actions; ChatGPT does not automatically synchronise the two.
- GitHub publication, editor identification and any production deployment remain unverified / out of Phase 00 scope.
- A three-week schedule assumes roughly 12–16 focused hours per week; adjust to actual availability.
Next phase / exact first action
1. Finish the handoff commit: replace the local docs/PROJECT_STATE.md with this version; inspect git diff -- docs/PROJECT_STATE.md; run git add docs/PROJECT_STATE.md; inspect git diff --cached --check and git diff --cached -- docs/PROJECT_STATE.md; then commit with git commit -m "docs: close Phase 00 with verified setup evidence".
2. Verify the handoff commit: run git status --short --branch and git log -1 --oneline; record the new hash as observed evidence at the next check-in. Refresh the ChatGPT Project reference copy separately if desired.
3. Begin Phase 01 — Sales Domain, Data Contract and Manual Examples: using prompts/phase_01.md, start by explaining the roles of created_date, expected_close_date and actual_close_date for one reference deal. Do not implement analytics before agreeing the commercial/data semantics.
Out of scope until later phases: CSV ingestion, analytics, pandas transformations, Streamlit UI, database, live integrations.
End-of-phase handoff template
Use these sections on every update:
1. Current phase / status / last completed phase / date.
2. Working functionality, with a concrete input -> output example.
3. Changed / important files and what they do.
4. Decisions and justified scope changes.
5. Commands, actual test outputs, commit, environment and live URL if any.
6. Concepts demonstrated and concepts needing reinforcement.
7. Remaining bugs / blockers and unverified claims.
8. Next phase, prerequisites and the exact next action.