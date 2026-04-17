# AI-assist.md — instructions for the AI assistant

> Read this **first** when you (the AI assistant) are invoked in this project directory. It tells you how to behave inside the lab's standard research workflow.

## 1. Orientation — what to read on entry

Before responding to any non-trivial request:

1. Read `PLAYBOOK.md` if you have not seen it in this conversation. It defines the workflow, the stages, and the AI roles.
2. Read `plan.md` to learn the **current stage**, milestones, and stage statuses.
3. Read the last 1–2 entries of `capture.md` for recent progress, issues, and open questions.
4. If the request involves a specific stage, read `stages/NN-<name>.md` for that stage.
5. If the request touches a past decision, scan `decisions/` for the relevant ADR.

Do this silently; do not narrate the reads to the user.

## 2. Per-stage AI role

Consult this table before acting. The role determines whether you draft, execute, or critique.

| #  | Stage                          | Your role             |
| -- | ------------------------------ | --------------------- |
| 0  | Setup                          | Executor              |
| 1  | Research Question & Hypothesis | Reviewer              |
| 2  | Literature Review              | Co-author             |
| 3  | Study Design                   | Co-author             |
| 4  | Data Acquisition               | Executor              |
| 5  | EDA                            | Co-author             |
| 6  | Preprocessing                  | Executor              |
| 7  | Baseline & SOTA Reproduction   | Human-guided Executor |
| 8  | Methods                        | Co-author             |
| 9  | Experimental Settings          | Co-author             |
| 10 | Experiments & Results          | Executor              |
| 11 | Discussion & Conclusion        | Co-author             |
| 12 | Writing                        | Co-author             |

**Role definitions**:

- **Executor** — you drive the work; the human sets parameters and reviews output.
- **Co-author** — you draft the artifact; the human edits substantively.
- **Reviewer** — the human drafts the artifact; you critique it against the stage's exit checklist and push back where needed.

## 3. Hard rules

These are non-negotiable. Violating them breaks the workflow's auditability.

- **Never** edit past `capture.md` entries. Only propose new ones (newest on top).
- **Never** mark a stage `approved` in `plan.md`. Only the human does that.
- Before writing in a stage doc, check that stage's status in `plan.md`. If `approved`, ask before modifying.
- When a decision turns out non-trivial, propose an ADR file under `decisions/` rather than burying the rationale in a stage doc.
- **Stages 1 and 2 form a cycle.** Treat them as paired:
  - Before starting stage 2, paraphrase the stage-1 research question back to the human and ask **at least one** clarifying question. Do not begin literature review until the human confirms understanding.
  - After each lit-review pass, write the **"Implications for the question"** section in `stages/02-literature-review.md` and ask the human whether to revise the question or exit the cycle.
  - Do not advance to stage 3 until **both** stages 1 and 2 are signed off in the same `plan.md` update.
- Before stage 7 starts, confirm `refs/survey.csv` has the `reproduce` and `priority` columns filled by the human.
- Stage 7 has explicit human gates (★) inside the activity loop — see `stages/07-baselines.md`. Do not skip them.

## 4. Status vocabulary

When updating `plan.md` (proposing changes only, never approving):

- `not-started` — no work yet.
- `in-progress` — you or the human are actively working.
- `in-review` — artifact drafted, awaiting human sign-off.
- `approved` — human has signed off. Re-opening requires logging in `capture.md` (see `PLAYBOOK.md` §6).

ADR statuses: `proposed | accepted | superseded-by-NNNN | rejected`.
Baseline statuses (in `stages/07-baselines.md`): `reproduced | deviated | abandoned`.

## 5. Iteration — re-opening an approved stage

If a downstream finding requires changing an upstream stage:

1. Propose flipping the stage's status from `approved` back to `in-progress` in `plan.md`.
2. Draft a `capture.md` entry explaining *why* (e.g., "Stage 10 results show baseline-vs-method gap is metric-sensitive → re-opening Stage 09 to add per-class F1").
3. If the reopen reflects a decision worth preserving, draft an ADR.

Never silently rewrite an approved stage.

## 6. Recommended skills per stage

The table below maps each stage to the skills you should proactively invoke when that stage is active. Skill names are the exact invocation strings. Consult each stage's own `## Recommended skills` section for per-skill rationale.

| # | Stage | Recommended skills |
| - | ------------------------------ | ------------------ |
| 0 | Setup                          | `update-config`, `less-permission-prompts`, `init` |
| 1 | Research Question & Hypothesis | `brainstorming` |
| 2 | Literature Review              | `paperclip-engine`, `focus`, `document-skills:pdf`, `document-skills:xlsx`, `document-skills:doc-coauthoring` |
| 3 | Study Design                   | `document-skills:doc-coauthoring`, `document-skills:canvas-design`, `brainstorming` |
| 4 | Data Acquisition               | `document-skills:docx`, `document-skills:pdf` |
| 5 | EDA                            | `document-skills:doc-coauthoring`, `document-skills:xlsx` |
| 6 | Preprocessing                  | `superpowers:test-driven-development`, `superpowers:verification-before-completion` |
| 7 | Baseline & SOTA Reproduction   | `superpowers:systematic-debugging`, `superpowers:verification-before-completion`, `superpowers:test-driven-development`, `superpowers:using-git-worktrees` |
| 8 | Methods                        | `document-skills:doc-coauthoring`, `brainstorming`, `superpowers:writing-plans` |
| 9 | Experimental Settings          | `document-skills:doc-coauthoring`, `superpowers:writing-plans` |
| 10 | Experiments & Results         | `superpowers:executing-plans`, `superpowers:dispatching-parallel-agents`, `superpowers:verification-before-completion`, `imagegen`, `document-skills:xlsx` |
| 11 | Discussion & Conclusion       | `document-skills:doc-coauthoring`, `focus` |
| 12 | Writing                       | `document-skills:doc-coauthoring`, `document-skills:docx`, `document-skills:pdf`, `document-skills:pptx` |

**Cross-cutting** (applies throughout the project):

- **`loop`** — schedule periodic wake-ups to draft the next `capture.md` entry (default: every two weeks). Human reviews and commits.
- **`superpowers:using-superpowers`** — the umbrella skill that reminds you to invoke other skills proactively.

**Rule**: when a stage is active and a recommended skill applies, invoke it via the Skill tool before answering — do not simulate the skill's workflow from memory.

## 7. Project-specific pointers (TODO — fill on first use)

> Lab member: replace this section with project-specific information.

- **Data location**: `<TODO: e.g., /scratch/yh60/sepsis-data/>`
- **Compute**: `<TODO: e.g., lab GPU server hostname; cluster account>`
- **Sensitive content / IRB**: `<TODO: yes/no; if yes, what restrictions apply to AI use — e.g., "do not include patient identifiers in any prompt">`
- **Lab conventions**: `<TODO: branch naming, commit format, anything else>`
