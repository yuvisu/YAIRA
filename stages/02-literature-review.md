# Stage 02 — Literature Review

**AI role**: Co-author
**Status**: not-started

> **This stage forms a cycle with Stage 01.** See `PLAYBOOK.md` §5. Do not start until Stage 01's "AI confirmation of understanding" step is complete.

## Purpose

Survey prior work that bears on the stage-1 research question, assess feasibility, identify available data, flag baselines and SOTAs for stage 7 reproduction, and tell the human whether the question needs revision.

## Inputs

- Stage 01's "Current draft" (research question, hypotheses, operational definitions).
- Available literature-search tools: `autoresearch/`, `paperclip-engine` skill, Google Scholar, PubMed, arXiv, Papers with Code.

## Activities

1. **Search.** AI runs queries across appropriate sources (autoresearch is one option; paperclip-engine and manual search are others). Aim for coverage, not just the most-cited.
2. **Populate `refs/survey.csv`**. One row per paper, with the columns described in `refs/survey.csv` (prior-art coverage, feasibility notes, data availability, baseline relevance, etc.).
3. **Triangulate**:
   - **Prior-art coverage**: does any paper already answer the stage-1 question? If yes, how completely?
   - **Feasibility analysis**: compute requirements (GPU hours, memory), ethics/IRB constraints, time, expertise. Flag blockers.
   - **Data availability**: which datasets are mentioned? Are they public, requestable, restricted? Licenses, cohorts, sample sizes.
   - **Baselines / SOTAs**: which methods set the bar? Add a `reproduce` column flag for stage 7 candidates.
4. **Write the narrative** (this file's "Narrative" section): synthesize findings, group by theme, identify gaps.
5. **Write the "Implications for the question" section** (mandatory): given what was found, is the stage-1 question (a) already answered, (b) needs sharpening, (c) needs broadening, (d) infeasible as stated, or (e) solid as-is?
6. **Hand back to Stage 01.** Human decides revise or exit. If revise: this stage's status flips back to `in-progress`; the next pass updates the survey delta rather than redoing it.

## Recommended skills

- **`paperclip-engine`** — biomedical paper search / retrieval / evidence synthesis. Primary driver of the survey; produces rows for `refs/survey.csv`.
- **`focus`** — rigorous section-by-section paper summarization with direct quotes. Use for the "Representative papers (deep dives)" subsection.
- **`document-skills:pdf`** — read downloaded paper PDFs when the `paperclip-engine` snippet is not enough.
- **`document-skills:xlsx`** — manage `refs/survey.csv`; can also scale the survey table into a proper spreadsheet if needed.
- **`document-skills:doc-coauthoring`** — structured co-authoring workflow for the "Narrative" and "Implications for the question" sections.

## Artifact(s)

- This file: narrative + implications + representative-papers detail.
- `refs/survey.csv`: one row per paper.
- `refs/` may also hold downloaded PDFs (or links if storage is constrained).

---

## Survey snapshot

> Auto-generated summary table from `refs/survey.csv`. Update each cycle.

- **Total papers reviewed**: `<N>`
- **Most recent paper year**: `<YYYY>`
- **Papers flagged for stage 7 reproduction**: `<N>`
- **Papers tagged as prior art that directly answer the question**: `<N>`

## Narrative

> Synthesize findings, grouped by theme. ~1–2 pages markdown.

`<TODO>`

## Representative papers (deep dives)

> For the top 3–5 papers, present in detail. Whether to focus on method-oriented or application-oriented detail depends on the project.

### Paper 1 — `<short title>` (`<author, year>`)

- **Setup**: `<dataset, task, evaluation>`
- **Method**: `<one paragraph>`
- **Headline metric**: `<value> on <dataset>`
- **Why it matters here**: `<relation to our question>`
- **Reproduce in stage 7?**: yes / no

### Paper 2 — ...

## Feasibility analysis

- **Compute**: `<TODO>`
- **Ethics / IRB**: `<TODO>`
- **Time**: `<TODO>`
- **Expertise**: `<TODO>`
- **Blockers**: `<TODO>`

## Data availability

| Dataset | Access     | License | Cohort / size | Relevant for | Notes |
| ------- | ---------- | ------- | ------------- | ------------ | ----- |
|         | public/req/restr |   |               |              |       |

## Implications for the question (mandatory section)

> AI fills this in after each lit-review pass. The human reads this to decide revise or exit the cycle.

**Status of the stage-1 question after this pass**: `<one of: already-answered | needs-sharpening | needs-broadening | infeasible | solid>`

**Reasoning**:

`<TODO>`

**Suggested revision (if any)**:

`<TODO>`

**Recommendation**: revise / exit cycle.

## Exit checklist

- [ ] `refs/survey.csv` has at least N papers (target N set by human; typical 30–60).
- [ ] Survey covers the top venues / authors / SOTAs in the area.
- [ ] Feasibility analysis is filled.
- [ ] Data availability table is filled.
- [ ] At least one row in `refs/survey.csv` has `reproduce: yes` (or the human has explicitly decided no baselines need reproduction, with reason).
- [ ] "Implications for the question" section is written.
- [ ] Latest cycle pass concludes the question is `solid`.
- [ ] Stage 01 and Stage 02 are signed off **together** in the same `plan.md` update.

---
**Sign-off** (signed in the same `plan.md` update as Stage 01)
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
