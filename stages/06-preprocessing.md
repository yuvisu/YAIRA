# Stage 06 — Data Preprocessing

**AI role**: Executor
**Status**: not-started

## Purpose

Turn `data/raw/` into a model-ready `data/processed/` artifact via a reproducible, version-controlled pipeline. No more hand-editing of CSVs.

## Inputs

- `data/raw/` (Stage 04).
- Stage 05 EDA findings (what to clean, impute, balance, encode, normalize).
- Stage 03 splits / leakage avoidance plan.

## Activities

1. Implement the pipeline in `src/preprocess.py` (or modules under `src/preprocess/`). Stages typically include:
   - **Missing-value handling**: drop rows/columns vs. impute (mean/median/MICE/learned). Document choice per column.
   - **Noise filtering**: outlier removal, smoothing, denoising.
   - **Class-imbalance handling**: oversampling (SMOTE), undersampling, class weights, focal loss — applied at the right place (training fold only, not test).
   - **Encoding**: categorical → one-hot / target encoding / embedding; text → tokenizer; image → resize / normalize.
   - **Normalization / scaling**: fit on train fold only.
2. Add a one-line invocation: e.g., `python -m src.preprocess --config configs/preprocess.yaml --in data/raw --out data/processed`.
3. Make the pipeline idempotent and reproducible: same inputs + same config → same outputs (record a manifest hash).
4. Write `src/preprocess.py`'s docstring describing each step.
5. Run end-to-end on raw data; verify processed artifact shape matches expectations from Stage 05.
6. Document each step's rationale in the table below.

## Artifact(s)

- `src/preprocess.py` (or `src/preprocess/`).
- `data/processed/<dataset-slug>/` outputs.
- This file with steps documented.
- Optional config file: `configs/preprocess.yaml`.

---

## Pipeline steps (documented)

| # | Step | Applied to | Method | Rationale | Where it runs (fit on train? all data?) |
| - | ---- | ---------- | ------ | --------- | --------------------------------------- |
| 1 | Missing values | `<columns>` | `<drop / median impute / ...>` | `<EDA found X% missing; ...>` | `<train-only fit / global>` |
| 2 | ... |   |   |   |   |

## Reproducibility

- **Invocation**: `<TODO>`
- **Config**: `<path/to/config>`
- **Random seed**: `<TODO>`
- **Output manifest hash**: `<TODO — recorded after first successful run>`

## Exit checklist

- [ ] `python -m src.preprocess ...` runs end-to-end on a fresh checkout, producing `data/processed/`.
- [ ] No leakage: train-fit-only steps are not fit on val/test.
- [ ] Each pipeline step has a row in the table above with rationale.
- [ ] Output shape matches Stage 05 expectations.
- [ ] Random seed and config are pinned; output manifest hash recorded.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
