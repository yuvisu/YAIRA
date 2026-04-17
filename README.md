# Research Project — `<project-name>`

A new research project scaffolded from the lab's standard workflow template (`YAIRA`).

> **New here? Read [`QUICKSTART.md`](QUICKSTART.md) first.** It has the copy-paste commands, the first prompt for Claude, and the per-stage loop on one page.

## What this is

A self-contained workspace for one research project, end to end: scoping → literature → data → methods → experiments → paper. The folder structure, stage documents, and tracking files implement a **human–AI interactive workflow**.

- Humans own the research question, judgment calls, and sign-off.
- AI assistants (e.g., Claude) act as **Executor**, **Co-author**, or **Reviewer** depending on the stage. See `PLAYBOOK.md`.

## How to use this template

1. Copy this directory and rename it to your project (e.g., `2026-sepsis-prediction/`).
2. Replace every `<placeholder>` you find — start with this README and `plan.md`.
3. Open `PLAYBOOK.md` and read it once.
4. Open `stages/00-setup.md` and begin.

## Where things live

| You want to... | Look in |
|---|---|
| Understand the workflow | `PLAYBOOK.md` |
| Tell the AI assistant how to behave | `AI-assist.md` |
| Know what stage you're in | `plan.md` |
| Catch up on recent progress | `capture.md` (top entries) |
| See significant decisions | `decisions/` |
| Read/update a stage's deliverable | `stages/NN-*.md` |
| Find the survey table | `refs/survey.csv` |
| Find a reproduced baseline | `baselines/<paper-slug>/` |
| Put raw / interim / processed data | `data/` |
| Notebooks | `notebooks/` |
| Project source code | `src/` |
| Generated figures / tables / reports | `artifacts/` |

## First-day quickstart

```bash
# 1. Copy the template
cp -r YAIRA/ my-project/
cd my-project/

# 2. Initialize git
git init
git add .
git commit -m "Initial scaffold from YAIRA"

# 3. Open stage 0 and follow it
$EDITOR stages/00-setup.md
```

Then point your AI assistant at this directory; it will read `AI-assist.md` and orient itself.
