# Stage 11 — Discussion & Conclusion

**AI role**: Co-author
**Status**: not-started

## Purpose

Interpret the Stage 10 results: what they say, what they mean, where they fail, what comes next. Output is the substantive content for the paper's Discussion and Conclusion sections (Stage 12 stitches them in).

## Inputs

- Stage 01 question and hypotheses.
- Stage 02 lit-review and gaps.
- Stage 07 reproduced baselines.
- Stage 10 results.

## Activities

1. AI drafts each subsection below.
2. Human edits substantively — owns the claims.
3. Cross-check: every hypothesis from Stage 01 is addressed (supported / not supported / inconclusive).
4. Cross-check: every limitation listed here also appears as a "threat to validity" or future-work item.
5. Identify next steps; promote the most concrete to ADRs or follow-up project candidates.

## Recommended skills

- **`document-skills:doc-coauthoring`** — structured co-authoring for interpretation, limitations, and conclusion.
- **`focus`** — when re-reading specific prior-work papers to ground the "Comparison to prior work" subsection with direct quotes.

## Artifact(s)

- This file.

---

## Findings

> What did the experiments show? Bullet 3–7 results. Each bullet ties to a specific table/figure ID from Stage 10.

- **F1**: `<TODO — finding statement; ref result table E#>`
- **F2**: ...

## Hypothesis verdicts

| Hypothesis (from Stage 01) | Verdict | Evidence | Caveats |
| -------------------------- | ------- | -------- | ------- |
| H1: ... | supported / not supported / inconclusive | F1, F2 |   |
| H2: ... |   |   |   |

## Interpretation

> What do the findings *mean*? Connect to mechanism, theory, or domain context. This is where the paper's contribution lives.

`<TODO>`

## Comparison to prior work

> How do these results sit relative to the baselines reproduced in Stage 07 and the prior art surveyed in Stage 02?

`<TODO>`

## Limitations

- **Data**: `<TODO>`
- **Method**: `<TODO>`
- **Evaluation**: `<TODO>`
- **Generalization**: `<TODO>`

## Threats to validity (revisited from Stage 03)

> Which a-priori threats from Stage 03 materialized, which were avoided, which need to be acknowledged honestly.

`<TODO>`

## Next steps

- **Immediate**: `<TODO — what would strengthen this paper before submission>`
- **Short-term follow-on**: `<TODO — natural sequels in 1–3 months>`
- **Long-term**: `<TODO — bigger questions opened up>`

## Conclusion (one paragraph)

`<TODO>`

## Exit checklist

- [ ] Every Stage-01 hypothesis has a verdict with evidence.
- [ ] Findings cite specific result-table / figure IDs.
- [ ] Limitations are honest and specific (not boilerplate).
- [ ] Threats-to-validity reconciled with Stage 03's a-priori list.
- [ ] Next steps include immediate, short-term, and long-term.
- [ ] Conclusion paragraph is publication-ready content (subject to Stage 12 polish).

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
