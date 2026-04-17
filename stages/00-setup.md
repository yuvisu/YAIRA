# Stage 00 — Setup

**AI role**: Executor
**Status**: not-started

## Purpose

Get the project workspace, environment, data access, and AI-assistant orientation in place so the rest of the workflow can run on a known baseline.

## Inputs

- This template directory, freshly copied and renamed.
- Lab-specific resources (compute, storage, data sources) the project will use.

## Activities

1. Initialize git: `git init`, first commit "Initial scaffold from YAIRA".
2. Create the project's Python (or other) environment:
   - `uv venv` or `conda create -n <project-name> python=3.x`
   - Add `pyproject.toml` / `requirements.txt` / `environment.yml` as appropriate.
3. Verify access to data sources (cloud bucket, hospital database, public download). Note credentials handling in `AI-assist.md`'s project-specific section.
4. Fill in the **"Project-specific pointers"** section at the bottom of `AI-assist.md` (data location, compute, IRB notes, lab conventions).
5. Set the project name and any `<TODO>` placeholders in `README.md` and `plan.md`.
6. Decide an initial milestone date for M1 (Stage 1↔2 cycle close) and put it in `plan.md`.
7. Optional: hook up a hosted git remote (GitHub / GitLab / lab Gitea).
8. Run a smoke test: a one-line script in `src/` that imports the env and prints versions. Commit it.

## Recommended skills

- **`update-config`** — tune `settings.json` (permissions, hooks, env vars) for this project.
- **`less-permission-prompts`** — scan past transcripts and auto-allowlist read-only commands to reduce friction.
- **`init`** — seed a project-level AI-instruction file. Treat its output as raw material for `AI-assist.md`'s project-specific section, not as a replacement.

## Artifact(s)

- This file, with the exit checklist completed.
- Initialized git repo + first commit.
- Working environment (`.venv` / conda env) reproducible from a pinned spec.
- `AI-assist.md` project-specific section filled in.

## Exit checklist

- [ ] `git log` shows the initial scaffold commit.
- [ ] Environment installs cleanly from spec on a fresh machine (or documented if not yet possible).
- [ ] Data sources accessible (or access requests submitted with target date).
- [ ] `AI-assist.md` project-specific section filled.
- [ ] M1 target date set in `plan.md`.
- [ ] Smoke test passes.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
