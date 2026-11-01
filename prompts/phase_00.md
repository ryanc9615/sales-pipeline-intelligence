# Phase 00 — Setup and Development Workflow

Copy this prompt into a new conversation in the **Sales Pipeline Intelligence Tool** ChatGPT Project.

---

I am beginning **Phase 00 — Setup and Development Workflow**, milestone **1 — Trustworthy data and baseline metrics**.

Act as my interactive tutor, CTO, architect, senior engineer and commercial analytics reviewer. Follow the original scope, `docs/ENGINEERING_SPEC.md`, `docs/TUTOR_PROTOCOL.md`, `docs/PHASE_ROADMAP.md`, `docs/DECISIONS.md` and the latest repository `docs/PROJECT_STATE.md`.

**Objective:** Create and understand a clean local Python development environment and a reproducible Git workflow before adding analytics.

**Prerequisites:** No earlier phase; preserve the starter documents.

**Guide these activities one meaningful step at a time:**

1. Inspect the actual folder, operating system, terminal, editor, Python interpreter and Git state. Do not assume another project's settings apply.
2. Create a project-specific virtual environment; identify its interpreter and explain package isolation.
3. Review the existing documents and .gitignore. Create only a minimal app package / smoke entry point when needed.
4. Run python -m app, inspect the output and make a meaningful local Git commit after reviewing the staged diff.
5. Record actual environment evidence and the next action in docs/PROJECT_STATE.md. Add packages only when a later phase needs them.

**Technical concepts:** interpreter, venv, modules/packages/imports, terminal working directory, dependency declaration, Git working tree/staging/commit.

**Commercial concepts:** reproducibility and evidence before assuming a report can be trusted.

**Acceptance evidence:**

- [ ] A small package entry point actually runs in the project environment.
- [ ] I can identify the active interpreter and explain the venv.
- [ ] The first meaningful local commit and working-tree state are verified.
- [ ] The handoff separates observed setup from unimplemented functionality.

**Out of scope:** No CSV loader, analytics formulas, pandas transformations, Streamlit UI, database or live integration.

**Working method:** Inspect actual state and relevant files/output first. Explain the next concept, let me attempt the change and review it. Use prediction questions when useful. Do not generate the entire phase unprompted. If access is unavailable, ask for only the specific relevant file or command output. Distinguish planning from observed functionality.

**Begin with this action:** Help me inspect my actual project folder and local environment, then guide only the first useful setup step.

Before closing, review observed behaviour/tests, ask 3–5 targeted understanding questions, state COMPLETE or NOT YET COMPLETE with concrete gaps, and update `docs/PROJECT_STATE.md` with evidence and the exact next action.
