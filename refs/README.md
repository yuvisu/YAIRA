# refs/

References for this project.

## Files

- `survey.csv` — the master survey table. One row per paper. Columns drive Stage 02 (lit review) and Stage 07 (baselines). The example row in the seed file documents allowed values; delete it on first real use.
- `*.bib` — BibTeX entries used by the paper draft (Stage 12). Keep `citation_key` consistent with `survey.csv`.
- Optional: downloaded PDFs of high-importance papers, organized as `pdfs/<citation_key>.pdf`. Watch licensing.

## Column glossary for `survey.csv`

| Column | Meaning |
| ------ | ------- |
| `paper_id` | Stable internal ID (e.g., `P0001`). |
| `citation_key` | BibTeX key. Must match `*.bib`. |
| `title`, `authors`, `year`, `venue`, `doi_or_arxiv` | Bibliographic. |
| `topic_tags` | Semicolon-separated tags for filtering. |
| `prior_art_coverage` | `none / partial / full` — does this paper answer our stage-1 question? |
| `feasibility_notes` | Compute, IRB, time, expertise constraints implied. |
| `data_availability` | Public / requestable / restricted; license; cohort. |
| `baseline_relevance` | `baseline / sota / tangential / none`. |
| `reproduce` | `yes / no / maybe`. **Stage 7 entry gate**: must be filled before Stage 7 starts. |
| `priority` | `1-5` (1 = highest) for Stage 7 ordering. |
| `code_url` | Best-known code location. |
| `notes` | Free-form. |
