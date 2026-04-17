# Stage 07 — Baseline & SOTA Reproduction

**AI role**: Human-guided Executor
**Status**: not-started

> **This stage has explicit per-step human gates (★).** Do not skip them. See `PLAYBOOK.md` §3.

## Purpose

For every paper the human flags as a baseline or SOTA, reproduce its results — first on the paper's own data, then on this project's data when applicable — and capture the reproduction process in an AutoSOTA-style ledger. Outcome is a verified bar that the proposed method (Stage 08) must clear.

## Inputs

- `refs/survey.csv` with `reproduce: yes/no/maybe` and `priority` columns filled by the human.
- `data/processed/` (Stage 06).
- Stage 03 splits / leakage plan (so the re-run on this project's data is comparable).

## Activities

For each row in `refs/survey.csv` with `reproduce: yes`, in priority order:

1. **Search code sources**: paper text → Papers with Code → GitHub by title/author → arXiv links.
2. ★ **Present candidates to human**: repo URL, stars, last commit, license, fork lineage. Human approves which fork/repo to use. Record the choice in the baseline's `OPTIMIZATION.md`.
3. **Clone** into `baselines/<paper-slug>/code/`. Pin commit hash.
4. **Set up isolated environment** in `baselines/<paper-slug>/env/`: prefer Docker; fall back to `uv venv` / conda. Record exact dependency versions.
5. **Run README quickstart**.
6. ★ **If quickstart fails**: log the failure, attempt standard fixes (env mismatches, missing data paths, deprecated APIs) up to N attempts (default N=3), then escalate to human with a written failure summary.
7. **Run published evaluation** on the paper's own data. Record the metric.
8. **Re-run on this project's data** (Stage 06 output) when applicable. Record the metric and any deviation from the paper's setup.
9. **Write `baselines/<paper-slug>/OPTIMIZATION.md`** — see template below.
10. ★ **Sign-off**: human marks the baseline `reproduced | deviated | abandoned` with a one-line reason.

## Recommended skills

- **`superpowers:systematic-debugging`** — use when README quickstart fails (step 6). Avoids flailing through env mismatches, deprecated APIs, and missing data paths.
- **`superpowers:verification-before-completion`** — before marking a baseline `reproduced`, confirm the metric within tolerance with evidence (not just a successful run).
- **`superpowers:test-driven-development`** — wrap each baseline's evaluation in a reusable test harness so re-runs (and project-data runs) are deterministic.
- **`superpowers:using-git-worktrees`** — isolate each baseline in its own worktree so their conflicting dependencies don't pollute the main project env.

## Artifact(s)

- `baselines/<paper-slug>/code/` — pinned clone.
- `baselines/<paper-slug>/env/` — Dockerfile or pinned env spec.
- `baselines/<paper-slug>/OPTIMIZATION.md` — per-baseline ledger.
- `baselines/<paper-slug>/results.json` — machine-readable metrics.
- This file with the aggregate leaderboard filled.

---

## Aggregate leaderboard

> One row per attempted baseline. `Δ` is `metric_on_project − metric_on_paper`.

| Paper-slug | Citation | Status | Metric (paper) | Metric (project) | Δ | Ledger | Notes |
| ---------- | -------- | ------ | -------------- | ---------------- | --- | ------ | ----- |
|            |          | reproduced/deviated/abandoned |   |   |   | `baselines/<slug>/OPTIMIZATION.md` |   |

## Per-baseline `OPTIMIZATION.md` template

> Save this template as `baselines/_OPTIMIZATION_template.md`. Each new baseline copies it.

```markdown
# Baseline: `<paper-slug>` — `<short citation>`

## Source
- Paper: <link>
- Repo (chosen): <URL>
- Commit hash: <40-char SHA>
- License: <SPDX>
- Why this fork: <human's note from ★ step 2>

## Environment
- Hardware: <GPU / CPU / RAM>
- OS: <ubuntu 22.04 / ...>
- Container: Dockerfile / conda env / pip freeze (link)
- Key dependency versions: <torch X.Y, cuda Z, ...>

## Reproduction on paper's own data
- Dataset: <name + version>
- Command: `<bash invocation>`
- Reported metric (from paper): <value>
- Our metric: <value>
- Match: yes / within tolerance / deviated by <delta>
- Notes / fixes applied: <bullet list>

## Run on this project's data
- Dataset: <our processed dataset>
- Command: `<bash invocation>`
- Metric: <value>
- Deviations from paper's setup (forced or chosen): <bullet list>

## Iteration log
| Attempt | Change | Result | Kept? |
| ------- | ------ | ------ | ----- |
| 1 | as-is | <error / metric> | <y/n> |
| 2 | <fix> | <result> | <y/n> |

## Status
reproduced | deviated | abandoned

## Sign-off
- Human reviewer: ___
- Date: ___
```

## Exit checklist

- [ ] Every `reproduce: yes` row in `refs/survey.csv` has a `baselines/<paper-slug>/` folder.
- [ ] Each folder has `code/` (pinned), `env/`, `OPTIMIZATION.md`, `results.json`.
- [ ] Aggregate leaderboard above is populated.
- [ ] Each baseline is signed off as `reproduced | deviated | abandoned` with a reason.
- [ ] Abandoned baselines have a documented reason (e.g., "no public code; emailed authors, no response by 2026-MM-DD").

---
**Sign-off** (closes the stage; per-baseline sign-offs live in each ledger)
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
