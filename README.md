# Climate-Change Effects on *Crithagra xantholaema* Habitat in Ethiopia 

[![DOI](https://img.shields.io/badge/DOI-10.1038%2Fs41598--025--20952--4-blue)](https://doi.org/10.1038/s41598-025-20952-4)
[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](http://creativecommons.org/publicdomain/zero/1.0/)
[![Made with R](https://img.shields.io/badge/Made%20with-R-276DC3?logo=r&logoColor=white)](https://www.r-project.org/)

R code and documentation accompanying the peer-reviewed article:

> **Gelete, T. B.**, Tulu, D., Yasin, K. H., & Kebede, E. (2025). Machine-learning predictions of climate-change effects on the nearly threatened bird species *Crithagra xantholaema* habitat in Ethiopia for conservation strategies. *Scientific Reports*, 15, 36972. https://doi.org/10.1038/s41598-025-20952-4

---

## 📖 Overview

The Yellow-throated Seedeater (*Crithagra xantholaema*) is a near-threatened songbird endemic to Ethiopia. Climate change is expected to alter the bioclimatic envelope this species depends on, but spatially explicit projections have been lacking. This study integrates **species occurrence data** with **bioclimatic and topographic predictors** in an **ensemble machine-learning species-distribution modelling (SDM) framework** to project current and future suitable habitat under multiple climate scenarios, and identifies priority areas for conservation.

## 📁 Repository structure

```
CrithagraXantholaemaHabitatAnalysis/
├── R/                       # Analysis scripts (rename "R code" folder to "R")
│   └── analysis.R
├── data/                    # Input data — see "Data sources" below
│   └── README.md
├── outputs/                 # Generated maps, figures, and tables
├── CITATION.cff             # Citation metadata (rendered as "Cite this repository")
├── LICENSE                  # CC0 1.0 Universal
└── README.md
```

> **Note on folder naming:** the original `R code` folder should be renamed to `R/` (without a space) — spaces in folder names break common R/CLI tooling and Continuous Integration.

## 🗂️ Data sources

| Layer | Source | License |
| --- | --- | --- |
| Species occurrence records | [GBIF](https://www.gbif.org/) | CC-BY-NC 4.0 |
| Bioclimatic variables (current & future) | [WorldClim v2.1](https://worldclim.org/data/index.html) | Free for academic use |
| Topographic variables (elevation, slope, aspect) | [SRTM](https://www.usgs.gov/centers/eros/science/usgs-eros-archive-digital-elevation-shuttle-radar-topography-mission-srtm) | Public domain |
| Land-cover | [ESA WorldCover](https://esa-worldcover.org/) | CC-BY 4.0 |

Raw input data are not redistributed in this repository to respect upstream licenses. See `data/README.md` for download instructions and the exact tile/scenario IDs used.

## ⚙️ Software requirements

- **R** ≥ 4.2.0
- Recommended: **RStudio** ≥ 2023.06

Key R packages:

```r
install.packages(c(
  # Spatial
  "raster", "terra", "sf", "sp",
  # Species-distribution modelling
  "dismo", "ENMeval", "biomod2", "maxnet",
  # Machine learning
  "randomForest", "caret", "xgboost",
  # Visualisation
  "ggplot2", "viridis", "tmap"
))
```

For full reproducibility, an `renv.lock` file pinning exact package versions is recommended (see [renv documentation](https://rstudio.github.io/renv/)).

## ▶️ Reproducing the analysis

```bash
git clone https://github.com/Tadelebedo/CrithagraXantholaemaHabitatAnalysis.git
cd CrithagraXantholaemaHabitatAnalysis
```

Then in R, run scripts in order (adjust file names to match your actual scripts):

```r
source("R/01_prepare_data.R")     # Clean occurrences, stack predictors
source("R/02_fit_models.R")       # Fit ensemble SDM
source("R/03_project_climate.R")  # Project under future climate scenarios
source("R/04_make_figures.R")     # Generate manuscript figures
```

Expected runtime: **~30–60 minutes** on a standard workstation (16 GB RAM).

## 📊 Key results

- Ensemble SDM achieves **AUC > 0.9** on held-out test data.
- Climate projections indicate **substantial range contraction** under high-emissions scenarios (SSP5-8.5) by 2050 and 2070.
- Identifies **priority conservation polygons** that retain suitability across all tested climate scenarios.

(See the published article for the full set of figures and discussion.)

## 📚 Citation

If you use this code or build on this work, please cite:

```bibtex
@article{gelete2025crithagra,
  title   = {Machine-learning predictions of climate-change effects on the nearly threatened bird species {Crithagra xantholaema} habitat in {Ethiopia} for conservation strategies},
  author  = {Gelete, Tadele Bedo and Tulu, Dereje and Yasin, Kediro Hussien and Kebede, Erana},
  journal = {Scientific Reports},
  volume  = {15},
  pages   = {36972},
  year    = {2025},
  doi     = {10.1038/s41598-025-20952-4}
}
```

A `CITATION.cff` file is included so GitHub displays a "Cite this repository" button automatically.

## 📜 License

Code in this repository is released under the [CC0 1.0 Universal](LICENSE) public-domain dedication. You are free to copy, modify, and redistribute, including for commercial purposes, without permission. Attribution via citation of the article above is appreciated.

## 👤 Author

**Tadele Bedo Gelete**
Researcher & Lecturer · School of Geography and Environmental Studies · Haramaya University, Ethiopia

📧 tadele.bedo@haramaya.edu.et
🔗 [LinkedIn](https://www.linkedin.com/in/tadele-bedo-212575298/) · [Google Scholar](https://scholar.google.com/citations?user=Ywzu2e8AAAAJ&hl) · [ORCID](https://orcid.org/0000-0001-5344-2580)

## 🙏 Acknowledgements

We thank Haramaya University and collaborating institutions for support during this study. Species occurrence data were obtained from GBIF and contributing observers, whose ongoing fieldwork makes this kind of analysis possible.

