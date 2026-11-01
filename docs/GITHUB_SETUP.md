# Setup and GitHub Workflow — Sales Pipeline Intelligence Tool

The starter archive is a **documentation scaffold**, with reference documents, phase prompts and a `.gitignore`. It intentionally contains no `.git` history, application implementation or installed environment. Phase 00 teaches the local setup. No GitHub repository or ChatGPT Project has been created by the archive.

## 1. Open the starter locally

Download and extract `sales-pipeline-intelligence-starter.zip`. Open the extracted `sales-pipeline-intelligence` folder in your editor. You may place it alongside your existing local learning projects; do not place it inside the Scenario Financial Engine repository or reuse that project's virtual environment.

Ask the tutor to inspect your actual environment, current directory and any existing Git state before running mutating commands. Adapt commands to the observed shell/OS.

For macOS / Linux, the intended Phase 00 sequence, once the current folder is verified, is:

```bash
python3 --version
git --version
python3 -m venv .venv
source .venv/bin/activate
python -c "import sys; print(sys.executable); print(sys.prefix); print(sys.base_prefix)"
```

Verify Python 3.12 or agree and record another compatible supported version. Avoid copying an absolute interpreter path from the other project. The tutor then guides the smallest `app` package and smoke entry point; runtime packages are introduced when needed.

During Phase 00, inspect whether a Git repository already exists. If it does not, initialise this project deliberately with `git init -b main`, review files, stage explicit paths and create a meaningful first commit. Do not overwrite or reinitialise an existing unrelated repository. Inspect the staged diff before every commit.

## 2. Publish only when the local project is ready

Create a new empty repository named `sales-pipeline-intelligence` in your own GitHub account. Public visibility suits a synthetic-data portfolio; private visibility is also possible during learning. Confirm the intended visibility and inspect for private data before publishing. Do not add a remote README if the local one already exists.

Use the actual repository URL returned by GitHub. The following URL is a template; replace `YOUR_USERNAME` before running it:

```bash
git remote add origin https://github.com/YOUR_USERNAME/sales-pipeline-intelligence.git
git push -u origin main
```

If a remote exists, inspect it with `git remote -v` instead of blindly adding or overwriting it. Use your established GitHub authentication; never paste passwords or tokens into chat.

Verify with `git status`, `git branch -vv`, the remote repository page and the latest commit. A local commit and a remote push are separate actions. This pack does not assert either has happened.

## 3. ChatGPT Project coaching setup

Use a ChatGPT Project named **Sales Pipeline Intelligence Tool**. Keep its learning context separate from Scenario Financial Engine.

- Put the text **below the divider** in `docs/TUTOR_PROTOCOL.md` into that Project's Instructions.
- Add `ORIGINAL_SCOPE.md`, `ENGINEERING_SPEC.md`, `PHASE_ROADMAP.md`, `TUTOR_PROTOCOL.md`, `CALCULATION_EXAMPLES.md` and `PHASE_PROMPTS.md` as reference files as useful.
- Keep the current repository `docs/PROJECT_STATE.md` as the handoff. Refresh a shared copy when needed; an old attached file is not automatically current.
- Start the first conversation with `prompts/phase_00.md`.

The prepared folder and files do not automatically create a ChatGPT sidebar Project, attach its references or apply its Instructions. Those actions must be performed in the ChatGPT Project interface unless a capable integration explicitly reports success.

## 4. Feature-by-feature Git workflow

Make one meaningful change; run the relevant check; update the handoff; review `git diff`; stage the intended files; review `git diff --staged`; commit with a useful message; push when ready. Do not commit `.venv`, secrets, real CRM exports or local caches.

Add tested exact runtime versions to `requirements.txt` and development requirements to `requirements-dev.txt` when packages are introduced. Do not invent version numbers from this planning pack or maintain conflicting dependency files.

Expected final commands, after the application actually exists:

```bash
python -m pip install -r requirements-dev.txt
python -m pytest
python -m streamlit run streamlit_app.py
```

These are future acceptance commands, not commands already executed by this setup task. Phase 08 verifies a clean installation and deployment using the then-current official host instructions.
