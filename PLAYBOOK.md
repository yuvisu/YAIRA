# PLAYBOOK — Research Project Standard Workflow

This is the lab's standard methodology for conducting a single research project. Read it once before starting a new project; refer back when stages get fuzzy.

---

## 1. Philosophy

Research is non-linear. Lit review changes the question. EDA changes the design. Results change the methods. The template makes that non-linearity **visible** — every revision is logged — instead of pretending the project ran straight.

Three operating principles:

1. **Humans own judgment.** The research question, ethics, study design choices, sign-off on every stage, and the paper's claims all belong to the human. AI assists; it does not adjudicate.
2. **AI accelerates execution and drafts.** AI does the searching, the boilerplate, the first cuts of writing, and the repeatable engineering. Humans edit, critique, and decide.
3. **Every approved stage is a checkpoint.** You can always go back, but going back is logged in `capture.md` (and, if the change is significant, in an ADR under `decisions/`).

## 2. Roles

Three AI roles, applied per stage:

- **Executor** — AI drives. AI does the work end-to-end (search, code, experiment runs, draft tables) under parameters the human sets. Human reviews the output.
- **Co-author** — AI drafts. AI produces the first version of the artifact (lit-review narrative, EDA notebook, methods writeup). Human edits substantively and owns the final form.
- **Reviewer** — AI critiques. The human drafts the artifact (research question, study design, experimental settings) and the AI checks it against the stage's exit checklist, asks clarifying questions, and pushes back where the artifact is unclear, untestable, or incomplete.

The human's role is constant: **question-setter, gatekeeper (sign-off on each stage), and final editor**.

## 3. The 13 stages

Each stage's full template is in `stages/NN-<name>.md`. This section is the playbook-level summary.

### Stage 0 — Setup (Executor)

Initialize the repo, set up the environment, verify data access, fill in the project-specific pointers in `AI-assist.md`. Exit when a fresh clone runs the project's smoke tests.

### Stage 1 — Research Question & Hypothesis (Reviewer) ⟲

Human articulates the initial research interest. AI paraphrases it back, lists assumptions, asks ≥ 1 clarifying question. Human confirms understanding. **This stage forms a cycle with stage 2 — see §5.**

### Stage 2 — Literature Review (Co-author) ⟲

AI executes the survey using available tools (autoresearch, paperclip-engine skill, manual search). The survey covers the usual fields plus **prior-art coverage**, **feasibility analysis**, **data availability**, and **baselines/SOTAs flagged for stage 7**. AI writes an "Implications for the question" section. Human decides whether to revise the stage-1 question or exit the cycle.

### Stage 3 — Study Design (Co-author)

AI drafts the design (design type, cohort / sampling frame, comparison structure, threats to validity) from stage-1 and stage-2 inputs. Human edits substantively — makes the design-type call, owns inclusion/exclusion criteria, decides IRB posture. AI flags gaps: selection bias, confounders, leakage between splits, sample-size adequacy.

### Stage 4 — Data Acquisition (Executor)

AI procures the data per stage 3's design: download scripts, access requests, format conversion, provenance/license documentation. Output lands in `data/raw/`. Exit when raw data is on disk and provenance is documented.

### Stage 5 — EDA (Co-author)

AI drafts an exploratory notebook covering: shape, dtypes, label distribution, distribution of important features, missingness rate per attribute, correlation matrix, outlier scan. Human edits, adds domain-specific cuts, flags surprises. Findings feed back into preprocessing (stage 6) and may re-open study design (stage 3).

### Stage 6 — Preprocessing (Executor)

AI implements the preprocessing pipeline in `src/preprocess.py`: missing-value handling (drop / impute), noise filtering, class-imbalance handling, encoding, normalization. Pipeline must be reproducible end-to-end on raw data with one command.

### Stage 7 — Baseline & SOTA Reproduction (Human-guided Executor) ★

This is the AutoSOTA-flavored stage. Human marks rows in `refs/survey.csv` with `reproduce: yes` and a priority. AI then, **with a human check-in at each ★**:

1. Searches for the codebase (paper text → Papers with Code → GitHub).
2. ★ Presents candidates; human picks the canonical fork.
3. Clones, pins commit hash, sets up an isolated env.
4. Runs the published evaluation; if it fails, attempts standard fixes; ★ escalates after N attempts.
5. Re-runs on this project's data when applicable.
6. Writes `baselines/<paper-slug>/OPTIMIZATION.md` (AutoSOTA-style ledger).

Each baseline is signed off as `reproduced | deviated | abandoned`. The aggregate leaderboard is in `stages/07-baselines.md`.

### Stage 8 — Methods (Co-author)

AI drafts the proposed method using the **Input → Process → Output** framework: precise enough that a competent ML engineer could re-implement from the doc alone. Human edits, owns the contribution.

### Stage 9 — Experimental Settings (Co-author)

AI drafts the settings by stitching from stages 3 (splits), 6 (data), 7 (baselines), 8 (method + ablations): experimental environment (hardware, software versions), data splits (which fold, what stratification), evaluation metrics (and *why* those metrics), the experiment list (which baselines, which ablations), reporting plan. Human edits substantively — especially picks the primary metric, decides which ablations matter, and signs off on the experiment list (this becomes the contract for Stage 10).

### Stage 10 — Experiments & Results (Executor)

AI runs every experiment in stage 9's list. Outputs: result tables (in `artifacts/tables/`), figures (in `artifacts/figures/`), confusion matrices, ROC curves, feature-importance plots, t-SNE. Exit when every planned run is done and recorded.

### Stage 11 — Discussion & Conclusion (Co-author)

AI drafts: findings (what the results say), interpretation (what they mean), limitations, threats to validity, comparison to prior work, next steps. Human edits and owns the claims.

### Stage 12 — Writing (Co-author)

AI drafts paper sections (intro, related work, methods, experiments, discussion, abstract) by stitching from earlier stage docs. Human edits paragraph by paragraph and owns the final manuscript.

## 4. Cross-cutting artifacts

### `plan.md` — updated in place

Single source of truth for milestones, the Gantt, and stage status. The human edits dates and statuses; the AI proposes edits when stages move.

### `capture.md` — append-only running log

Biweekly entries. Each entry: progress, issues, solutions/decisions, next two weeks. AI never edits past entries. AI proposes the next entry; the human reviews and commits. `artifacts/reports/` holds rendered PDF/PPTX exports for advisor meetings.

### `decisions/` — ADRs

One file per significant decision (method choice, dataset cut, evaluation protocol, environment lock). Use it when: (a) the choice has multiple defensible options, (b) future-you would ask "why did we do this?", or (c) the decision will be cited in the paper. Capture log links to ADRs by ID.

### Status vocabulary

Stage statuses (in `plan.md`): `not-started | in-progress | in-review | approved`.
ADR statuses: `proposed | accepted | superseded-by-NNNN | rejected`.
Baseline statuses: `reproduced | deviated | abandoned`.

## 5. The Stage 1 ↔ 2 scoping cycle

Stages 1 and 2 are paired. Both must close together; only after the cycle stabilizes can stage 3 start.

```
            ┌─────────────────────────┐
            │ Stage 1: Question draft │
            └──────────┬──────────────┘
                       │
                       ▼
        ┌──────────────────────────────┐
        │ AI confirms understanding ★  │
        └──────────┬───────────────────┘
                   │
                   ▼
   ┌──────────────────────────────────────┐
   │ Stage 2: Lit review + feasibility    │
   │   - prior-art coverage               │
   │   - feasibility (compute, IRB, time) │
   │   - data availability                │
   │   - baselines/SOTAs flagged          │
   └──────────┬───────────────────────────┘
              │
              ▼
   ┌──────────────────────────────────┐
   │ AI writes "Implications for Q"   │
   └──────────┬───────────────────────┘
              │
              ▼
            ★ Human decides:
            Revise question? ──yes──▶ back to Stage 1
                  │
                  no
                  │
                  ▼
            Sign off both → Stage 3
```

Each iteration is logged under `## Cycle history` in `stages/01-research-question.md`. Major reframings become ADRs.

## 6. Working with the AI assistant

**How to invoke**: open this project directory in your AI tool of choice. The assistant should read `AI-assist.md` automatically; if it doesn't, paste a "please follow `AI-assist.md`" prompt to start.

**When to ask the AI to draft (Co-author)**: lit-review narrative, study design, EDA, methods writeup, experimental settings, discussion, paper sections, biweekly capture entry.

**When to ask the AI to execute (Executor)**: setup, data acquisition, preprocessing pipeline, baseline reproduction, experiment runs, results aggregation.

**When to ask the AI to review (Reviewer)**: research question. Hand it your draft and ask "critique against the stage's exit checklist."

**When to *not* use the AI**:

- Initial ideation about *what is interesting* — that's a human judgment.
- Ethical, clinical, or IRB-sensitive decisions.
- Anything involving patient identifiers or other restricted content unless your `AI-assist.md` project-specific section explicitly approves it.
- Final claims in the paper. AI drafts; humans claim.

## 7. Iteration — re-opening an approved stage

The rule: a downstream finding can re-open an upstream stage, but it must be logged.

1. Flip the stage's status from `approved` back to `in-progress` in `plan.md`.
2. Add a `capture.md` entry explaining why.
3. If the reopen reflects a decision worth preserving, write an ADR.

Common re-opens:

- Stage 5 EDA finds severe class imbalance → re-open Stage 3 to revisit cohort definition.
- Stage 7 baselines are stronger than expected → re-open Stage 1 to sharpen the contribution.
- Stage 10 results are metric-sensitive → re-open Stage 9 to add per-class metrics.
- Reviewer feedback on the paper → re-open whichever stage they hit.

## 8. Conventions

- **Branches**: `stage-NN/<short-slug>` for active work; `main` is signed-off content.
- **Commits**: prefix with `[stage NN]`; explain *why* in the body when non-trivial.
- **Notebooks** live in `notebooks/`; productionized code lives in `src/`. Notebooks are exploratory and may be messy; `src/` is reproducible.
- **Figures and tables** live in `artifacts/`, generated by code. Don't hand-edit them.
- **Biweekly report rendering**: when you need a PDF/PPTX for an advisor meeting, render the latest `capture.md` entry (for now: copy/paste into slides; Phase C will automate).

## 9. Quickstart — first day on a new project

```bash
cp -r YAIRA/ <project-name>/
cd <project-name>/
git init && git add . && git commit -m "Initial scaffold"

# Open and skim
$EDITOR PLAYBOOK.md          # this file
$EDITOR AI-assist.md         # AI behavior rules; fill in the project-specific pointers
$EDITOR plan.md              # set milestone target dates
$EDITOR stages/00-setup.md   # follow it; check off the exit checklist

# Then move to stage 1
$EDITOR stages/01-research-question.md
```

Open the project in your AI assistant and start the stage 1 ↔ 2 cycle.
