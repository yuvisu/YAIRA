# QUICKSTART

The condensed end-to-end flow. For the full methodology, see `PLAYBOOK.md`.

## 1. Copy the template

```bash
cp -r YAIRA/ <project-name>/
cd <project-name>/
git init && git add . && git commit -m "Initial scaffold from YAIRA"
```

## 2. Fill the first placeholders (~5 min)

- **`README.md`** — project name + one-line description.
- **`AI-assist.md`** — the "Project-specific pointers" section at the bottom (data location, compute, IRB posture, lab conventions).
- **`plan.md`** — target date for **M1** (Stage 1↔2 cycle close).

## 3. Start Claude in the project

```bash
claude
```

## 4. First prompt to Claude

> Read `AI-assist.md` and follow it. Then read `PLAYBOOK.md`, `plan.md`, and the top of `capture.md`. I'm starting this project fresh — let's begin Stage 00 (Setup).

Claude will orient, then walk through Stage 00.

## 5. Per-stage working loop

For each stage:

1. **You**: "Let's start Stage `NN`." (or "Let's continue Stage `NN`.")
2. **Claude**: reads `stages/NN-*.md`, adopts its role (Executor / Co-author / Reviewer), and acts.
3. **You**: edit, push back, approve.
4. **You**: sign off in the stage file and flip the row in `plan.md` to `approved`.
5. **Claude** (every ~2 weeks): drafts the next `capture.md` entry; you review and commit.

**Claude never marks a stage `approved` — only you do.**

## 6. Special gates

### Stage 1 ↔ 2 scoping cycle (mandatory)

- Claude **must** paraphrase your stage-1 question back and ask ≥ 1 clarifying question before starting Stage 02.
- After each lit-review pass, Claude writes **"Implications for the question"** in `stages/02-literature-review.md` and asks: revise the question or exit the cycle.
- Both stages sign off **together**. Do not advance to Stage 03 until both are `approved`.

### Stage 07 baseline reproduction (per-step gates ★)

- Fill `reproduce` and `priority` columns in `refs/survey.csv` **before** starting. Claude won't begin without this.
- Claude presents each candidate codebase for your approval before cloning.
- Claude escalates to you after N failed reproduction attempts.
- Each baseline gets signed off as `reproduced | deviated | abandoned`.

## 7. Iteration — re-opening a signed-off stage

Research is non-linear. To re-open an approved stage:

1. Flip its status in `plan.md` from `approved` back to `in-progress`.
2. Add a `capture.md` entry explaining why.
3. If the change is significant, write an ADR in `decisions/`.

## 8. Where things live (cheat sheet)

| Need to... | Go to |
| --- | --- |
| Understand the workflow | `PLAYBOOK.md` |
| Configure AI behavior | `AI-assist.md` |
| See current stage | `plan.md` |
| Catch up on progress | top of `capture.md` |
| Find past decisions | `decisions/` |
| Work on a stage | `stages/NN-*.md` |
| Survey table | `refs/survey.csv` |
| Reproduced baseline | `baselines/<paper-slug>/` |
| Figures / tables / reports | `artifacts/` |

## 9. Daily rhythm (suggested)

- **Start of session**: tell Claude which stage you're in; ask it to read `capture.md`'s latest entry.
- **During**: let Claude draft / execute / critique based on the stage's AI role.
- **End of session**: if a non-trivial decision was made, have Claude draft an ADR. Commit.
- **Every ~2 weeks**: ask Claude to draft the next `capture.md` entry; review, edit, commit. Optionally render for advisor meeting.

## 10. When *not* to rely on Claude

- Initial ideation — "is this an interesting question?" is your call.
- Ethics / IRB / clinical judgment.
- Anything involving restricted data unless `AI-assist.md`'s project-specific section explicitly permits it.
- Final claims in the paper. Claude drafts; you claim.
