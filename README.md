# THRIVE-Belize Needs Assessment: Co-occurring Adolescent Health Risks and Life-Skills Needs

## Overview

This repository contains the analysis code for the study "Co-occurring Adolescent Health Risks and Life-Skills Needs at Toledo Community College in Punta Gorda, Belize: A School-Based Needs Assessment" (manuscript in preparation).

The study is a census-style cross-sectional survey of all students in Forms 1-3 at the only secondary school in Punta Gorda, Toledo District, Belize (May 2025; analytic N = 497). Indicators were selected from the full survey item inventory by criteria that made no reference to the planned intervention, and the resulting needs map was then used to evaluate the proposed THRIVE-Belize school life-skills program, module by module.

## Key Features

- **Program-blind indicator selection**: 27 risk/need indicators chosen by criteria fixed before modeling (anchorable construct; prevalence at least 10%; missingness at most 10%; non-redundancy), documented item by item
- **Co-occurrence analysis**: cumulative risk/need burden tested against a same-marginals independence benchmark
- **Latent class analysis**: 2-6 class solutions on all 497 students with full-information handling of item missingness; class count fixed by a predefined rule (lowest BIC with a 25-student minimum class size)
- **Regularized Ising network**: eLasso/IsingFit with case-drop and nonparametric bootstrap stability checks
- **Randomized list experiments**: difference-in-means estimation of nine sensitive experiences with corrected crossed treatment arms
- **Priority and support cascade**: care-continuum-style concentration analysis of the survey's life-safety indicator, with a support-gap level
- **Sensitivity analysis**: all narrative-critical results reproduced on the consent-affirmed subsample
- **Verification checks throughout**: every analysis block prints its own checks and the script halts on any failure

## Repository Structure

```
THRIVE-Belize-Needs-Assessment/
|-- README.md                  # This file
|-- tcc_analysis4_paper1.Rmd   # Main analysis pipeline (knits to Word)
|-- .gitignore                 # Excludes data and generated outputs
|-- data/
    |-- README.md              # Data availability and placement instructions
```

## Data Availability

The deidentified student-level dataset and codebook are **not** included in this repository. They are available upon reasonable request from the corresponding author (Mario Morales, mariomorales@arizona.edu), subject to approval by Toledo Community College and local health partners and a data-use agreement protecting student privacy. See `data/README.md` for placement instructions once access is granted.

## Requirements

### R Version

R >= 4.5.2

### Required Packages

```r
install.packages(c(
  "poLCA",      # Latent class analysis
  "bootnet",    # Network estimation and bootstrap stability
  "IsingFit",   # eLasso Ising network estimator
  "qgraph",     # Network drawing
  "tidyverse",  # Data manipulation and plotting
  "knitr",      # Reporting
  "flextable",  # Publication tables (Word export)
  "officer",    # Word formatting backend
  "ggrepel",    # Non-overlapping figure labels
  "ragg"        # High-resolution figure devices
))
```

## Reproducing the Analysis

1. Obtain the dataset (`tcc_data_paper1.csv`) from the corresponding author (see Data Availability).
2. Place the file one directory **above** the repository root (the script reads `../tcc_data_paper1.csv`), or edit the `read.csv()` path at the top of the script.
3. Knit `tcc_analysis4_paper1.Rmd` (R Markdown, Word output). All random seeds are fixed; every table and figure in the manuscript and its supplement is regenerated into `tcc_analysis4_outputs/`, and the script stops with an error if any internal verification check fails.

## Ethics

The study was approved by the Belize Ministry of Health and Wellness (IRB No. GEN/147/01/25(42)Vol.VI, May 2, 2025). Passive parental consent procedures were followed; participation was anonymous and voluntary.

## Funding

Fieldwork was supported by a Tinker Field Research Grant from the Tinker Foundation, administered by the Center for Latin American Studies at the University of Arizona, and by a University of Arizona Graduate and Professional Student Council (GPSC) travel grant (Spring 2025).

## Citation

A citation will be added when the manuscript is published. Until then, please cite this repository:

> Morales M. THRIVE-Belize Needs Assessment: analysis code. GitHub repository, 2026. https://github.com/yeridu/THRIVE-Belize-Needs-Assessment
