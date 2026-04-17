# Stage 09 — Experimental Settings

**AI role**: Co-author
**Status**: not-started

## Purpose

Lock the experimental protocol — environment, splits, metrics, the full experiment list — *before* running anything in Stage 10. Once approved, no settings change without re-opening this stage.

## Inputs

- Stage 03 splits / leakage plan.
- Stage 06 processed data and preprocessing pipeline.
- Stage 07 baselines (and their reproduced metrics).
- Stage 08 method + ablation candidates (especially the "Suggested ablations" list).

## Activities

1. AI drafts the settings below, stitching from the inputs above: proposed environment pin, split scheme, candidate metrics with rationale, the full experiment list (every baseline from Stage 07, the proposed method, every ablation from Stage 08, a hyperparameter-sensitivity sweep), and a reporting plan.
2. Human edits substantively. Human **owns**: primary-metric choice, which ablations matter, final experiment list (this becomes the contract for Stage 10).
3. AI re-reads the human-edited draft and flags remaining gaps (missing ablations, metric–question mismatch, leakage, missing seeds, hardware mismatch with baselines).
4. Iterate until satisfied. Once approved, this is the contract for Stage 10.

## Recommended skills

- **`document-skills:doc-coauthoring`** — structured workflow for drafting environment, splits, metrics, experiment list, and reporting plan.
- **`superpowers:writing-plans`** — turn the experiment list into an executable plan that Stage 10 can follow without reinterpretation.

## Artifact(s)

- This file.

---

## Experimental environment

- **Hardware**: `<GPU model + count, RAM, CPU>`
- **OS / drivers**: `<TODO>`
- **Software versions**: `<TODO — pin Python, torch/tf, cuda, key libs>`
- **Container / env spec**: `<path to Dockerfile or env file>`
- **Random seeds**: `<list of seeds — typically ≥ 3 for reporting mean ± std>`

## Data splits

- **Split scheme**: `<train/val/test sizes; or k-fold k=...; or temporal split date>`
- **Stratification key**: `<TODO>`
- **Source of splits**: `<paper-defined / our split / both reported>`
- **Leakage check applied**: `<TODO — describe>`

## Evaluation metrics

| Metric | Why this metric | Primary / secondary | Threshold or comparison |
| ------ | --------------- | ------------------- | ----------------------- |
|        |                 |                     |                         |

> Mismatch alarm: if the primary metric does not directly answer the stage-1 question, fix it now.

## Experiment list

| ID | Method | Variant | Hyperparameters | Splits | Seeds | Expected runtime |
| -- | ------ | ------- | --------------- | ------ | ----- | ---------------- |
| E1 | Baseline A (Stage 07) | as published | — | test | s1,s2,s3 | ~Xh |
| E2 | Baseline B (Stage 07) | as published | — | test | s1,s2,s3 | ~Xh |
| E3 | Ours (Stage 08) | full | from §08 table | test | s1,s2,s3 | ~Xh |
| E4 | Ours — ablation: remove X | | | test | s1,s2,s3 | ~Xh |
| E5 | Ours — ablation: replace Y with Z | | | test | s1,s2,s3 | ~Xh |
| E6 | Hyperparameter sensitivity (sweep over <param>) | | grid: ... | val | s1 | ~Xh |

## Reporting plan

- **How metrics are aggregated across seeds**: mean ± std (or median + IQR; justify if not mean/std).
- **Statistical tests** (if applicable): `<paired t-test / Wilcoxon / bootstrap CI / ...>`
- **Result-table format**: `<which columns, decimals, bolding rule>`

## Exit checklist

- [ ] AI-drafted first cut was produced.
- [ ] Human edited substantively; primary-metric choice and final experiment list are the human's call.
- [ ] Environment pinned (versions + container).
- [ ] Splits match Stage 03 plan; leakage check described.
- [ ] Primary metric directly answers the stage-1 question.
- [ ] Experiment list covers: every Stage 07 baseline, the proposed method, every ablation from Stage 08, hyperparameter sensitivity.
- [ ] Multiple seeds for headline numbers.
- [ ] Reporting plan (aggregation + stats) is concrete.
- [ ] AI gap-flag pass applied; gaps either filled or recorded as open risks.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
