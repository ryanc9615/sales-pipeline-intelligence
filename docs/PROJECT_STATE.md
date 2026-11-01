Sales Pipeline Intelligence Tool — Project State
Keep this factual and update it at the end of each working phase. Planning documents are not proof of implementation. The current repository copy takes precedence over an old uploaded snapshot.

Current position
- Phase: 00 — Setup and Development Workflow
- Status: IN PROGRESS — local environment and initial package execution established; Git commit and final phase gate pending
- Last completed phase: None
- State updated: 1 November 2026, from learner-supplied terminal output and follow-up messages
- Current milestone: 1 — Trustworthy data and baseline metrics
Working functionality
- The starter planning and tutoring pack exists locally, including scope, engineering specification, roadmap, manual calculation examples and phase prompts.
- A minimal Python package has been created with app/__init__.py and app/__main__.py.
- Observed: python -m app printed Hello World before the entry point was revised.
- Learner-reported: after replacing the temporary print statement with a main() smoke entry point, the command worked. The exact latest output and current file contents have not yet been pasted for independent review.
- No CSV loader, validation, pandas calculations, forecasting, Streamlit UI, HTTP exercise, third-party runtime dependencies or automated application tests have been implemented or verified.
- No remote repository or live deployment has been evidenced.
Repository / important files
- app/__init__.py: observed empty package marker.
- app/__main__.py: minimal smoke entry point; originally observed as print("Hello World"), then edited by learner. Verify and restage its final contents before committing.
- .gitignore: inspected; excludes .venv/, __pycache__/, Python/test artefacts and common local secrets.
- README.md: entry point and setup order.
- docs/ORIGINAL_SCOPE.md: user brief and explicit planning assumptions.
- docs/ENGINEERING_SPEC.md: V1 input, calculation, UI and delivery contract.
- docs/PHASE_ROADMAP.md: phases, hours and acceptance gates.
- docs/TUTOR_PROTOCOL.md: copy-ready ChatGPT coaching instructions.
- docs/PHASE_PROMPTS.md and prompts/phase_00.md through phase_09.md: guided conversation starters.
- docs/CALCULATION_EXAMPLES.md: independent reference values, including precision and boundary cases.
- docs/DECISIONS.md: baseline choices and parked ideas.
- docs/PORTFOLIO_EVIDENCE.md: completion-evidence checklist and insight template.
- docs/GITHUB_SETUP.md: local setup, publication and ChatGPT reference instructions.
- data/README.md and tests/README.md: planned work only, not runtime data or passing tests.
Decisions / architecture
- Python + pandas + Streamlit remain the planned V1 stack; pandas and Streamlit are not installed for this project yet.
- A project-specific .venv is used for package isolation. No external packages have been added in Phase 00.
- A minimal python -m app entry point is retained as a repeatable setup smoke test; it is not an analytics implementation.
- Original calculation contract is unchanged: one GBP CSV snapshot, integer pence, Decimal probabilities, per-deal half-up rounding, and explicit snapshot/reporting dates.
- Current open pipeline remains distinct from period-eligible pipeline; win rate and observed creation-cohort conversion must not be confused with historical stage transitions.
- Local HTTP exercise remains a future learning task; no live CRM integration or separate backend.
- No scope-changing decision or deployment has occurred. See docs/DECISIONS.md.
Verification
- Operating system / shell: macOS (Darwin), /bin/zsh, verified by uname -s and echo "$SHELL".
- Local project directory: ~/Documents/Projects/LearningAI/sales-pipeline-intelligence (pwd output supplied).
- Base Python: Python 3.12.5; command -v python3 resolved to /Library/Frameworks/Python.framework/Versions/3.12/bin/python3.
- Virtual environment: created with python3 -m venv .venv; activated in zsh. command -v python and sys.executable resolved to the project's .venv/bin/python; sys.prefix resolved to the project's .venv; sys.base_prefix resolved to /Library/Frameworks/Python.framework/Versions/3.12.
- Smoke command: python -m app produced Hello World in learner-shared terminal output; subsequent revised main() version reported working, but its exact output has not been independently inspected in chat.
- Git version: 2.39.3 (Apple Git-146).
- Git local repository: git init -b main succeeded; git status --short --branch initially showed No commits yet on main and untracked starter files.
- Git ignore evidence: git check-ignore -v identified .gitignore line 2 for .venv/ and line 5 for app/__pycache__/.
- Staging evidence: starter files and package were staged using explicit paths; git status --short showed additions. git diff --cached --stat was inspected. At that point, app/__main__.py was empty in the staged snapshot; the learner subsequently edited it, so restaging and full staged-content review are required.
- First commit / clean tree: NOT YET VERIFIED. No commit hash, post-commit status or remote URL supplied.
- Application tests observed passing: None; no automated application tests exist yet. The smoke run is not an analytics test.
- Live URL: Not deployed.
- Editor: Not positively identified from supplied output.
Learning outcomes
- Demonstrated: working directory; system and shell identification; base interpreter versus active virtual environment; expected differences between sys.prefix and sys.base_prefix; package execution with python -m app; Git installation versus repository initialisation; basic ignore-rule inspection.
- Corrected understanding: staging captures a file version when git add runs; a later working-tree edit does not automatically update the staged version.
- Needs reinforcement / final Phase 00 check: read an actual staged diff; explain why restaging is needed after editing; distinguish working tree, index and commit; explain what the smoke test does and does not prove; demonstrate commit and clean-tree verification.
- Later reinforcement: pipeline denominators, snapshot limitations, integer money, pandas grouping/filtering, HTTP boundaries and independent test oracles.
Known issues / blockers
- No identified technical blocker. Finish the current Git workflow without adding packages or analytics.
- Latest local app/__main__.py content has not been independently displayed; do not assume the previously staged empty version reflects the runnable entry point.
- The initial local Git commit is pending. This attached handoff is a prepared replacement; placing it in the Mac's repository and committing it still requires a local action.
- GitHub publication, editor details and any ChatGPT Project reference sync have not been established by terminal evidence.
- A three-week schedule assumes roughly 12–16 focused hours/week; adjust to actual availability.
Next phase / exact first action
- Current phase: 00 — Setup and Development Workflow; do not advance to Phase 01 yet.
- Exact next action: Save this updated file as docs/PROJECT_STATE.md in the local project. In the active .venv, rerun python -m app and inspect its output. Then run git add app/__main__.py docs/PROJECT_STATE.md, inspect git diff --cached --check, git diff --cached --stat and git diff --cached, and confirm staged content is correct before committing.
- After review: Create a meaningful local commit; verify git log -1 --oneline and git status --short --branch, record the observed commit hash/status in this handoff, and answer 3–5 targeted Phase 00 understanding questions before marking the phase COMPLETE.
- Out of scope until later phases: CSV ingestion, analytics, pandas transformations, Streamlit UI, database, live integrations.
End-of-phase handoff template
Use these sections on every update:
1. Current phase / status / last completed phase / date.
2. Working functionality, with a concrete input → output example.
3. Changed / important files and what they do.
4. Decisions and justified scope changes.
5. Commands, actual test outputs, commit, environment and live URL if any.
6. Concepts demonstrated and concepts needing reinforcement.
7. Remaining bugs / blockers and unverified claims.
8. Next phase, prerequisites and the exact next action.