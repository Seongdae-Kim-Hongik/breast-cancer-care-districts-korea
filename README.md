# Breast cancer treatment ratios across Korean districts — analysis code

Analysis code for the manuscript "Later first marriage and fewer public sports facilities mark Korean districts with higher breast cancer treatment ratios" (Seongdae Kim, Hongik University).

This repository contains **code and model design files only**. It does not contain source statistics, the analysis-ready panel, expected counts, boundary files, adjacency graphs or result tables.

## Inputs the code expects
- Annual district counts of persons treated for breast cancer (C50), NHIS Regional Medical Care Utilization Statistics, 2011–2024 (KOSIS).
- Female resident-registration population by district and age group (Ministry of the Interior and Safety; KOSIS).
- National Health Insurance 298-disease age-specific patient counts (KOSIS) for indirect age standardization.
- District covariates listed in `design/config.json` (KOSIS, Korea Community Health Survey, national health-screening statistics, sports-facility registers).
- Cancer-registry district incidence (KOSIS DT_117N_A11109) for the descriptive concordance check.

The analysis-ready panel derived from these public sources is available from the author on reasonable request.

## Layout
| Folder | Contents |
|---|---|
| `code/00_primary_model.R` | Reference model: negative binomial, BYM2 district effect, RW1 + iid year effects (R-INLA) |
| `code/01_main_chain/` | Panel checks, reference fit, set comparison, calendar windows, maps and emerging hot-spot summaries, sensitivity suite, registry comparison |
| `code/02_multiverse/` | 200-specification subset-stability analysis (seed 20261104 + specification number) |
| `code/03_space_time_structures/` | Knorr–Held I–IV, Spatial+ and alternative neighbour/prior fits |
| `code/04_exposure_timing_and_age80/` | Ten-year-lag and 2000–2004 baseline exposures; age-80+ adjustment |
| `code/05_predictive_checks/` | Posterior predictive checks and sensitivity combination |
| `design/` | Model specification: forced controls, exploratory covariate sets, negative controls, rules |

## Software
R 4.x with INLA (single thread, `num.threads = "1:1"`), sf, spdep, jsonlite; Python 3.9+ with pandas, numpy, geopandas, matplotlib. Scripts were written for the author's directory layout; edit the input paths at the top of each script before running.

## Licence
MIT (code). Source statistics remain subject to the terms of their providers.
