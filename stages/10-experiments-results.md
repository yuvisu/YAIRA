# Stage 10 — Experiments & Results

**AI role**: Executor
**Status**: not-started

## Purpose

Run every experiment in Stage 09's experiment list. Produce result tables, figures, and analyses ready to be discussed in Stage 11 and written up in Stage 12.

## Inputs

- Stage 09 experiment list (the contract).
- Stage 06 processed data.
- Stage 07 baseline implementations.
- Stage 08 proposed method.

## Activities

1. For each experiment in Stage 09's list:
   - Implement the run script in `notebooks/10-<eid>-<method>.ipynb` or `src/run/<eid>.py`.
   - Execute. Log to `artifacts/runs/<eid>/`.
   - Aggregate metrics across seeds.
2. Build the headline result table (`artifacts/tables/results.md` and `.csv`).
3. Build the standard figures: confusion matrix, ROC curve, calibration plot, learning curves, ablation comparison bar chart.
4. Build analysis figures: feature importance (tree-based), result visualization (t-SNE / UMAP of learned embeddings), error analysis cuts.
5. Update the run-status table below as runs complete.
6. If results suggest revising Stage 09 settings (e.g., metric-sensitive findings) or Stage 08 method (e.g., a fix unlocks a much stronger ablation), flag in `capture.md` and propose re-opening that stage.

## Recommended skills

- **`superpowers:executing-plans`** — execute the Stage 09 plan step by step, with review checkpoints.
- **`superpowers:dispatching-parallel-agents`** — launch independent experiments (different seeds, different ablations) in parallel.
- **`superpowers:verification-before-completion`** — confirm every experiment completed with evidence (logs + metrics on disk) before marking `done`.
- **`imagegen`** — generate publication-ready figures where matplotlib alone is insufficient.
- **`document-skills:xlsx`** — assemble `artifacts/tables/results.csv` and derived pivot tables.

## Artifact(s)

- `notebooks/10-*.ipynb` and/or `src/run/*.py` per experiment.
- `artifacts/runs/<eid>/` raw run logs and per-seed metrics.
- `artifacts/tables/results.{md,csv}` aggregated.
- `artifacts/figures/10-*.{png,pdf}`.
- This file with run-status table populated and a summary of headline findings.

---

## Run status

| Exp ID | Method/Variant | Seeds done | Mean metric | Std | Status | Notes |
| ------ | -------------- | ---------- | ----------- | --- | ------ | ----- |
| E1 |   |   |   |   | not-started / running / done / failed |   |
| E2 |   |   |   |   |   |   |
| E3 |   |   |   |   |   |   |
| E4 |   |   |   |   |   |   |
| E5 |   |   |   |   |   |   |
| E6 |   |   |   |   |   |   |

## Headline result table

> Final form lives in `artifacts/tables/results.md`; mirror or summarize here.

`<TODO>`

## Headline figures

- Confusion matrix: `artifacts/figures/10-confusion.png`
- ROC: `artifacts/figures/10-roc.png`
- Ablation bar chart: `artifacts/figures/10-ablation.png`
- Feature importance: `artifacts/figures/10-feature-importance.png`
- Result visualization (t-SNE / UMAP): `artifacts/figures/10-tsne.png`

## Initial summary of findings

> One paragraph. Detailed interpretation belongs in Stage 11.

`<TODO>`

## Exit checklist

- [ ] Every experiment in Stage 09 is `done` or has a documented `failed` reason.
- [ ] Headline table aggregated across seeds.
- [ ] Standard figures generated.
- [ ] Run logs and per-seed metrics archived under `artifacts/runs/`.
- [ ] Initial summary of findings drafted.
- [ ] Any required upstream re-opens (Stage 08 / 09) have been initiated.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
