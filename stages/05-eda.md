# Stage 05 — Exploratory Data Analysis

**AI role**: Co-author
**Status**: not-started

## Purpose

Build a clear empirical picture of the data before designing preprocessing and methods. Surface surprises early enough to feed back into stages 3, 4, or even 1.

## Inputs

- `data/raw/` (Stage 04).
- Stage 03 cohort definition and outcome variable.

## Activities

1. AI drafts `notebooks/05-eda.ipynb`. Notebook covers (at minimum):
   - **Shape & dtypes** per dataset / table.
   - **Label distribution** (class balance, class counts).
   - **Distribution of important features** — histograms, KDE, or boxplots; broken out by label where meaningful.
   - **Missingness rate per attribute** — bar chart or heatmap.
   - **Correlation matrix** (numeric features).
   - **Outlier scan** — IQR or z-score flags.
   - **Domain-specific cuts** — e.g., per cohort, per site, per time window.
2. Human edits the notebook: add domain-specific exploration, flag surprises, write commentary cells.
3. Summarize the notebook's findings in this file's "Findings" section.
4. If findings imply changes upstream (e.g., severe imbalance → revisit Stage 03 cohort, or missing key columns → revisit Stage 04 acquisition), flag in `capture.md` and propose re-opening the relevant stage.

## Artifact(s)

- `notebooks/05-eda.ipynb` (committed; cleared outputs are OK if rerunnable).
- This file with "Findings" written.
- Key figures exported to `artifacts/figures/05-eda/`.

---

## Findings (summary; full detail in the notebook)

### Data shape

`<TODO — N rows, K features, train/val/test sizes if pre-split>`

### Label distribution

`<TODO — counts and proportions per class; if regression, distribution stats>`

### Important features

`<TODO — distributions; differences across labels>`

### Missingness

`<TODO — which columns have what missingness rate; any patterns>`

### Correlations

`<TODO — strong correlations to outcome; multicollinearity concerns>`

### Surprises / red flags

`<TODO — anything that should change upstream stages>`

## Implications for downstream stages

- **Preprocessing (Stage 06)**: `<TODO>`
- **Methods (Stage 08)**: `<TODO — e.g., need to handle imbalance, need feature engineering>`
- **Upstream re-open?**: `<TODO — none / Stage 3 / Stage 4 / Stage 1; if not none, log in capture.md>`

## Exit checklist

- [ ] Notebook covers shape, label distribution, feature distributions, missingness, correlations, outliers.
- [ ] Domain-specific cuts added by human.
- [ ] Key figures exported to `artifacts/figures/05-eda/`.
- [ ] "Findings" and "Implications" sections written.
- [ ] Any required upstream re-opens have been initiated.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
