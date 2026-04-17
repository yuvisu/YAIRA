# Stage 04 — Data Acquisition

**AI role**: Executor
**Status**: not-started

## Purpose

Procure the data described in Stage 02's data-availability table and Stage 03's cohort definition. Land it in `data/raw/` with full provenance.

## Inputs

- Stage 02 data-availability table.
- Stage 03 inclusion/exclusion criteria, IRB status.

## Activities

1. For each dataset to acquire:
   - Locate source (URL, API, hospital extract, vendor delivery).
   - Submit access requests if needed; track status.
   - Download / extract / convert. Save under `data/raw/<dataset-slug>/`.
   - Compute and record SHA-256 of the raw files.
   - Document provenance (source URL, query parameters, date downloaded, version).
2. Write the **Data Provenance Table** below — one row per dataset.
3. Confirm licenses are recorded and compatible with the project's intended outputs (paper, code release).
4. Flag any dataset that is restricted (PHI, license-restricted) so downstream stages handle it correctly.

## Recommended skills

- **`document-skills:docx`** — draft IRB amendments, data-use agreements, or access-request letters when acquisition requires paperwork.
- **`document-skills:pdf`** — parse data-dictionary PDFs, license agreements, and vendor documentation.

## Artifact(s)

- This file with provenance table filled.
- `data/raw/<dataset-slug>/...` containing the raw files.
- `data/raw/<dataset-slug>/PROVENANCE.md` per dataset (URL, date, SHA-256, license, access notes).

---

## Data Provenance Table

| Dataset | Source | Date acquired | Version / snapshot | License | SHA-256 (manifest) | Access notes |
| ------- | ------ | ------------- | ------------------ | ------- | ------------------ | ------------ |
|         |        |               |                    |         |                    |              |

## Access requests in flight

| Dataset | Submitted | Expected | Owner | Status |
| ------- | --------- | -------- | ----- | ------ |
|         |           |          |       |        |

## Sensitive-data handling

> If any acquired data is PHI or otherwise restricted: document the storage location, access-control posture, and AI-use restriction here. Cross-reference Stage 03's IRB notes.

`<TODO>`

## Exit checklist

- [ ] Every dataset in Stage 02's table is either acquired or has an access request tracked.
- [ ] Provenance table is filled for acquired datasets.
- [ ] Each `data/raw/<dataset-slug>/` has a `PROVENANCE.md`.
- [ ] Licenses recorded; incompatibilities flagged.
- [ ] Sensitive-data handling documented if applicable.

---
**Sign-off**
- Human reviewer: ___
- Date: ___
- Status: [draft | in-review | approved]
