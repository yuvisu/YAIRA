# baselines/

One subfolder per reproduced baseline (Stage 07).

## Layout per baseline

```
baselines/<paper-slug>/
├── code/                  # cloned repo, pinned to a commit hash (gitignored from this repo)
├── env/                   # Dockerfile or pinned dependency spec
├── OPTIMIZATION.md        # AutoSOTA-style ledger (see template below)
└── results.json           # machine-readable metrics
```

`<paper-slug>` is a short, filesystem-safe identifier (e.g., `2024-smith-deeper`). Use the `citation_key` from `refs/survey.csv` when in doubt.

## Per-baseline ledger template

Copy `_OPTIMIZATION_template.md` (in this folder) when starting a new baseline.
