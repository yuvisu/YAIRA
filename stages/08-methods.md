# Stage 08 — Methods

**AI role**: Co-author
**Status**: not-started

## Purpose

Specify the proposed method precisely enough that another competent ML engineer could re-implement it from this document alone. Use the **Input → Process → Output** framework.

## Inputs

- Stage 01 question and hypotheses.
- Stage 02 lit-review gaps (what novelty is justified).
- Stage 06 preprocessing schema (input shape).
- Stage 07 baselines (what bar to beat).

## Activities

1. AI drafts an initial method writeup using the IPO skeleton below.
2. Human edits substantively — owns the contribution.
3. AI proposes a reference implementation skeleton in `src/methods/<method-name>.py` (interfaces + stubs; full impl can be in Stage 10's prep).
4. AI flags any ablation that the method's structure naturally invites; carry these into Stage 09.

## Artifact(s)

- This file with IPO and rationale filled.
- `src/methods/<method-name>.py` skeleton (or actual implementation if convenient).
- Optional: a method diagram in `artifacts/figures/08-method.<ext>`.

---

## Method name

`<TODO — short, memorable>`

## Input

> What the method consumes. Be exact about shape, dtype, range, and assumed preprocessing.

`<TODO>`

## Process

> The method itself. Subsections as needed (e.g., encoder / decoder / loss). Include equations where they clarify, pseudocode where it helps.

`<TODO>`

### Hyperparameters (initial)

| Hyperparameter | Initial value | Rationale | Search range (Stage 09) |
| -------------- | ------------- | --------- | ----------------------- |
|                |               |           |                         |

## Output

> What the method emits. Shape, dtype, semantics. How predictions are converted to the metric.

`<TODO>`

## Why this method (rationale)

> Tie back to the gaps from Stage 02. What novel claim does this method support? Why is it expected to outperform the baselines from Stage 07?

`<TODO>`

## Suggested ablations (carry into Stage 09)

- `<TODO — e.g., "remove component X to test contribution Y">`
- `<TODO>`

## Reference implementation skeleton

`<TODO — pointer to src/methods/<method-name>.py with at least the class signature and forward() stub>`

## Exit checklist

- [ ] Input / Process / Output sections written precisely enough to re-implement.
- [ ] Hyperparameters table filled with initial values and rationale.
- [ ] Rationale ties to Stage 02 gaps.
- [ ] Ablation candidates listed.
- [ ] Reference skeleton exists in `src/methods/`.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
