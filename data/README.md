# LMD_HR_PUBLIC

Analysis code for the manuscript **HORMONE RECEPTOR STATUS SWITCH AND METASTATIC CENTRAL NERVOUS SYSTEM TROPISM DURING BREAST CANCER PROGRESSION TO LEPTOMENINGEAL DISEASE**.

## Repository structure
- `code/`: analysis code and R Markdown report
- `data/`: not included (see **Data availability**)

## Data availability
Deidentified individual-level data are not publicly available due to privacy/IRB restrictions and are not included in this repository.  
To rerun the full analysis, authorized users should place the required input files in `data/` and update file paths in the code if needed.

## Reproducible environment (renv)
This project uses the R package `renv` to record package versions.

```r
install.packages("renv")
renv::restore()
```
## How to run
1. Clone/download this repository.
2. Open LMD_HR_PUBLIC.Rproj in RStudio.
3. Knit or run the main analysis report: code/LMD_Analysis_QSU_PUBLIC.Rmd.
## Notes
- Rendered reports (HTML/PDF) are not tracked in the repository.
- A Zenodo DOI will be created from a tagged GitHub Release for the archived manuscript version.
## Contact
Bo Gu (sybo2199@stanford.edu)