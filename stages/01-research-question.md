# Stage 01 — Research Question & Hypothesis

**AI role**: Reviewer
**Status**: not-started

> **This stage forms a cycle with Stage 02.** See `PLAYBOOK.md` §5 for the full loop semantics. Both stages are signed off together.

## Purpose

Articulate a specific, testable research question (and one or more hypotheses) that survives feasibility scrutiny from the literature review.

## Inputs

- Human's initial research interest (rough is fine).
- Domain context the human brings.

## Activities

1. **Human writes the initial research interest** below in "Initial draft": domain, phenomenon of interest, what they hope to learn, and (if any) initial hypothesis.
2. **AI confirmation of understanding** (mandatory):
   - AI paraphrases the question back in its own words.
   - AI lists the assumptions it inferred (target population, success criterion, scope).
   - AI asks **at least one** clarifying question (e.g., "Is the goal prediction or causal estimation?", "Which patient cohort?", "What metric defines success?").
   - Human confirms or corrects.
3. **Refined draft**: human (with AI as scribe) writes the refined question, hypotheses, and operational definitions in "Current draft" below.
4. **Hand off to Stage 02** (Literature Review).
5. **Re-entry from Stage 02**: after each lit-review pass, return here, read the "Implications for the question" section in `stages/02-literature-review.md`, and decide:
   - Question is **solid** → proceed to sign-off.
   - Question needs **revision** → flip status back to `in-progress`, edit "Current draft", append a `Cycle history` entry, and re-enter Stage 02.

## Artifact(s)

- This file, with "Current draft" filled and "Cycle history" populated.

---

## Initial draft (rough, by human)

> *(Domain, phenomenon, what we hope to learn, any initial hypothesis. Stream-of-thought is fine.)*

`<TODO>`

## AI's paraphrase + assumptions + clarifying questions

> *(AI fills this in during step 2. Human edits/corrects.)*

**Paraphrase**: `<TODO>`

**Assumptions inferred**:
- `<TODO>`

**Clarifying questions**:
1. `<TODO>`

## Current draft (refined, post-clarification)

**Research question**: `<TODO — one sentence>`

**Hypotheses**:
- **H1**: `<TODO>`
- **H2** (optional): `<TODO>`

**Operational definitions**:
- Population / unit of analysis: `<TODO>`
- Outcome / target variable: `<TODO>`
- Predictor / treatment variables: `<TODO>`
- Success criterion (metric + threshold or comparison): `<TODO>`

## Cycle history

> One line per iteration of the Stage 1↔2 loop.

- Iter 1 (`<YYYY-MM-DD>`): initial Q — `<TODO>`

## Exit checklist

- [ ] AI has paraphrased the question and human has confirmed understanding.
- [ ] Current draft contains question + hypotheses + operational definitions.
- [ ] Stage 02 has been entered at least once.
- [ ] Cycle has stabilized: latest pass through Stage 02 concludes "question is solid".
- [ ] Question and hypotheses are specific, testable, and not already answered by prior work.
- [ ] Major reframings during the cycle are recorded as ADRs.

---
**Sign-off** (signed in the same `plan.md` update as Stage 02)
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
