# LMD_HR_PUBLIC

Analysis code and de-identified data for the manuscript **HORMONE RECEPTOR STATUS SWITCH AND METASTATIC CENTRAL NERVOUS SYSTEM TROPISM DURING BREAST CANCER PROGRESSION TO LEPTOMENINGEAL DISEASE**.

## Repository structure
- `code/LMD_Analysis_QSU_PUBLIC.Rmd`: full analysis (R Markdown report)
- `data/LMD_cohort_deidentified.csv`: one row per patient (n = 141)
- `data/LMD_HR_history_deidentified.csv`: one row per ER/PR/HER2 assessment (336 rows)
- `renv.lock`, `renv/`: recorded R package versions

## Data availability
The de-identified individual-level data needed to reproduce all results in the manuscript are included in `data/`.
The data were de-identified following the HIPAA Safe Harbor method (45 CFR 164.514(b)(2)):
- Institutional patient identifiers were replaced by arbitrary study IDs (`P001`–`P141`).
- All calendar dates were replaced by the number of days since breast cancer diagnosis (diagnosis = day 0).
- Date of birth was replaced by age at diagnosis in whole years (all patients < 90).
- Geographic (zip code) and insurance information were removed, as were variables not used in the analysis.
- Race categories with very small counts (Pacific Islander, Unknown) were combined into "Other", as in the analysis.

These changes do not affect any result: the analysis reproduces the manuscript results exactly
(multiple imputation with `mice`, m = 20, seed = 1024).

## Reproducible environment (renv)
This project uses the R package `renv` to record package versions (analysis run with R 4.5.2).

```r
install.packages("renv")
renv::restore()
```

## How to run
1. Clone/download this repository.
2. Open `LMD_HR_PUBLIC.Rproj` in RStudio (the code locates `data/` with `here::here()`).
3. Knit `code/LMD_Analysis_QSU_PUBLIC.Rmd`.

## Data dictionary

### `LMD_cohort_deidentified.csv`

| Variable | Description |
|---|---|
| Study ID | De-identified patient ID |
| Race | White, Asian, Black, Other |
| Ethnicity | Non-Hispanic, Hispanic/Latino, Unknown |
| Age at Diagnosis | Age (years) at breast cancer diagnosis |
| Censor Status | 1 = died, 0 = censored |
| Death Status Note | Vital status text when an exact date of death was not available (e.g., Alive, Unconfirmed); blank otherwise |
| Days Dx to Death | Days from diagnosis to death |
| Days Dx to Last Contact | Days from diagnosis to last contact (patients without a confirmed date of death) |
| Days Dx to HR Assessment | Days from diagnosis to baseline hormone receptor assessment |
| ER, PR, HER2 | Baseline receptor status: 1 = positive, 0 = negative, NF = not found |
| Subtype | lumA, lumB, HER2, TN, NF |
| Stage | Stage at diagnosis (0–4; NF = not found; analysed as 1–4, others treated as missing) |
| Grade | Tumor grade (1–3; NF = not found) |
| 1st Met Site | Site of first metastasis |
| Days Dx to 1st Met | Days from diagnosis to first metastasis |
| Days Dx to Brain Met | Days from diagnosis to brain metastasis (blank = none) |
| Days Dx to LMD | Days from diagnosis to leptomeningeal disease |

### `LMD_HR_history_deidentified.csv`

| Variable | Description |
|---|---|
| Study ID | De-identified patient ID (links to the cohort file) |
| Days Dx to HR Assessment | Days from diagnosis to the receptor assessment (blank = date not found) |
| ER, PR, HER2 | Receptor status at that assessment: 1 = positive, 0 = negative, NF = not found |

Negative day values indicate an event recorded shortly before the diagnosis date; the analysis sets these to 0.

## Notes
- Rendered reports (HTML/PDF) are not tracked in the repository.
- A Zenodo DOI will be created from a tagged GitHub Release for the archived manuscript version.

## Contact
Bo Gu (sybo2199@stanford.edu)
