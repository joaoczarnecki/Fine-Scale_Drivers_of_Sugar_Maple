# Fine-Scale Drivers of Sugar Maple (*Acer saccharum*) Habitat Suitability at its Northern Range Limit

[![Status](https://img.shields.io/badge/Status-Accepted%202026-blue)]()
[![R](https://img.shields.io/badge/R-4.5.2-276DC3?logo=r)](https://www.r-project.org/)

## Overview

This repository contains the data and reproducible analysis code supporting the manuscript:

> **Czarnecki de Liz, J.P.**, Thiffault, N., Coops, N.C., Morin-Bernard, A., & Achim, A. (*in press*). Fine-Scale Drivers of Sugar Maple (*Acer saccharum*) Habitat Suitability at its Northern Range Limit.

At its northern range limit, climate change is increasing the uncertainty about the persistence of sugar maple (*Acer saccharum*). To inform climate adaptation strategies, we developed a high-resolution species distribution model using a Random Forest algorithm to identify currently suitable habitats, determine their primary environmental drivers, and project future shifts. The model, based on 3 664 ground plots and built with fine-scale (20 m) topographic, soil, and climate data, demonstrated high predictive accuracy (76.4%) when tested against a spatially independent dataset (AUC = 0.868). Under a near-future climate scenario (SSP3–7.0, 2021–2040), we project a net increase in suitable habitat, with gains (~16%) significantly outweighing losses (~3%).

**Keywords:** adaptive silviculture, spatial analysis, LiDAR-derived terrain metrics, wall-to-wall mapping

---

## Repository Structure

```
Fine_Scale_Sugar_Maple_Habitat_Suitability/
│
├── script/
│   └── 000_Fine-Scale_Drivers_Sugar_Maple_clean.Rmd   # Full reproducible analysis
│
├── database/
│   └── undisturbed_plots_sf_env_clim_4th_inv_study_area_PET.csv  # Plot-level dataset
│
└── 000_Fine-Scale_Drivers_Sugar_Maple_Code_Rmd.html   # Rendered HTML output
```

---

## Data

The dataset (`undisturbed_plots_sf_env_clim_4th_inv_study_area_PET.csv`) contains plot-level observations from the 4th Quebec Forest Inventory, filtered to undisturbed stands within the study area. Variables include:

- **Response variable:** Sugar maple basal area proportion (habitat suitability proxy)
- **LiDAR-derived structural predictors:** Topographic Wetness Index and other fine-scale terrain metrics at 20 m resolution
- **Soil predictors:** Cation Exchange Capacity and related fertility indicators
- **Bioclimatic predictors:** Mean Coldest Month Temperature, precipitation, and wind exposition
- **Topographic variables:** elevation, slope, aspect

---

## Reproducible Analysis

The full analysis pipeline is documented in `000_Fine-Scale_Drivers_Sugar_Maple_clean.Rmd` and covers:

1. Data preparation and spatial filtering
2. Spatial cross-validation design (Valavi et al. 2019 / `blockCV`)
3. Forward Feature Selection (`CAST` package)
4. Random Forest model fitting and tuning (`caret`)
5. Model evaluation: AUC, TSS, threshold-based performance metrics
6. Down-sampling to address class imbalance
7. Accumulated Local Effects (ALE) plots for variable interpretation
8. Habitat suitability mapping and future projections (SSP3–7.0, 2021–2040)

The rendered HTML output (`000_Fine-Scale_Drivers_Sugar_Maple_Code_Rmd.html`) provides a fully navigable version of the analysis with all results, figures, and code.

---

## Requirements

Analysis was conducted in **R 4.5.2**. Main packages:

| Package | Purpose |
|---|---|
| `caret` | Random Forest modelling and tuning |
| `CAST` | Forward Feature Selection, spatial cross-validation |
| `blockCV` | Spatial block cross-validation |
| `sf` | Spatial data handling |
| `tidyverse` | Data manipulation and visualization |
| `iml` | ALE plots and model interpretation |
| `ggplot2` | Figures |

To reproduce the analysis, open `000_Fine-Scale_Drivers_Sugar_Maple_clean.Rmd` in RStudio and knit, or run sequentially in an R session.

---

## Citation

> Citation details will be updated upon publication.

---

## Authors

- **João Paulo Czarnecki de Liz** — Département des sciences du bois et de la forêt, Faculté de foresterie, de géographie et de géomatique, Université Laval, Québec, Canada
- **Nelson Thiffault** — Canadian Forest Service, Natural Resources Canada, Québec, Canada
- **Nicholas C. Coops** — Department of Forest Resources Management, University of British Columbia, Vancouver, Canada
- **Alexandre Morin-Bernard** — Département des sciences du bois et de la forêt, Faculté de foresterie, de géographie et de géomatique, Université Laval, Québec, Canada
- **Alexis Achim** — Département des sciences du bois et de la forêt, Faculté de foresterie, de géographie et de géomatique, Université Laval, Québec, Canada

---

## License

Code is released under the [MIT License](LICENSE). Data use is subject to Quebec Forest Inventory data sharing policies.

---

## Acknowledgements

We thank the Direction des inventaires forestiers (Ministère des Ressources naturelles et des Forêts du Québec) for access to forest inventory data.
