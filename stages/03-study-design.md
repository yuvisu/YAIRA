# Stage 03 — Study Design

**AI role**: Co-author
**Status**: not-started

## Purpose

Choose the design that lets the data answer the stage-1 research question. Lock cohort / sampling frame, comparison structure, and ethics/IRB posture before touching data.

## Inputs

- Signed-off Stage 01 (research question, hypotheses, operational definitions).
- Signed-off Stage 02 (data availability table, prior-art designs, feasibility constraints).

## Activities

1. AI drafts the design below, stitching from stage-1 / stage-2 inputs and prior-art design patterns. AI proposes: design type, inclusion/exclusion criteria candidates, split/comparison structure, leakage-avoidance plan, a-priori threats to validity.
2. Human edits substantively. Human **owns**: the design-type call, inclusion/exclusion thresholds, IRB posture, and any clinical/ethical judgment.
3. AI re-reads the human-edited draft and flags remaining gaps (selection bias, confounders, leakage, sample-size adequacy, generalization claim alignment).
4. Iterate until both sides are satisfied.

## Artifact(s)

- This file.
- Optional: a study-design diagram (CONSORT-style flowchart, patient-timeline figure, train/val/test split diagram). Save under `artifacts/figures/03-study-design.<ext>`.

---

## Design type

> Pick one (or describe a hybrid):
> - Case-control
> - Cohort (prospective / retrospective)
> - Cross-sectional
> - RCT-style train/test
> - Cross-domain / cross-site evaluation
> - k-fold cross-validation (justify k)
> - Time-split / temporal hold-out
> - Other

`<TODO>`

## Cohort / sampling frame

- **Inclusion criteria**: `<TODO>`
- **Exclusion criteria**: `<TODO>`
- **Estimated sample size after filtering**: `<N>`
- **Power / sufficiency rationale**: `<TODO>`

## Comparison structure

- **Comparison groups** (for case-control / cohort / RCT-style): `<TODO>`
- **Splits** (for predictive ML): train / val / test sizes; stratification key; temporal split date if applicable.
- **Leakage avoidance plan**: `<TODO>`

## Patient timeline / observation window (if clinical)

> Optional: ASCII timeline or link to figure.

`<TODO>`

## Ethics / IRB

- **IRB required?**: yes / no / exempt
- **IRB protocol number**: `<TODO>`
- **Data-sharing constraints**: `<TODO>`
- **AI-use restrictions** (e.g., "no PHI in prompts"): `<TODO>`

## Threats to validity (a priori)

- **Internal**: `<TODO — confounders, selection bias, measurement>`
- **External**: `<TODO — generalization to other sites / cohorts / time periods>`
- **Construct**: `<TODO — does the outcome variable measure what we mean?>`

## Exit checklist

- [ ] AI-drafted first cut was produced.
- [ ] Human edited substantively and made the design-type call.
- [ ] Design type matches the question (predictive vs. causal vs. descriptive).
- [ ] Inclusion/exclusion criteria written precisely enough to apply.
- [ ] Sample-size sufficiency justified.
- [ ] Splits / comparison structure defined; leakage plan stated.
- [ ] IRB status resolved.
- [ ] Threats-to-validity section written.
- [ ] AI gap-flag pass applied; outstanding concerns either addressed or recorded as open risks in `capture.md`.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
