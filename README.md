# 🇦🇪 UAE Property Valuator - R Reproducibility Project

![R](https://img.shields.io/badge/R-4.0+-276DC3?logo=r&logoColor=white)
![RStudio](https://img.shields.io/badge/RStudio-IDE-75AADB?logo=rstudio&logoColor=white)

This project is a reproduction of the UAE Property Valuator machine learning pipeline. The original project was built using Python (Jupyter Notebooks) as an end-to-end MLOps pipeline. As part of a reproducible research initiative, we successfully recreated the exploratory data analysis (EDA) and machine learning modeling stages entirely in **R**.

---

##  Team Members

| Name | Student Number |
| :--- | :--- |
| [Mukhammadkodir Abdusalomov] | [474664] |
| [Mirzakalonboy Khamidov] | [474561] |
| [Elbek Majidov] | [474***] |

---

##  Language Translation (Python to R)

**Original Implementation:** Python
- Used libraries: `pandas`, `scikit-learn`, `xgboost`, `lightgbm`, `matplotlib`, `seaborn`
- Environment: Jupyter Notebooks (`.ipynb`)

**Reproduced Implementation:** R
- Used libraries: `tidyverse` (`dplyr`, `ggplot2`), `caret`, `xgboost`, `lightgbm`, `randomForest`, `glmnet`
- Environment: R Markdown (`.Rmd`)

The primary goal was to validate the reproducibility of the original Python-based ML results using the R programming ecosystem. We successfully translated the data manipulation, statistical modeling, and model evaluation components from Python to R.

---

##  Dependencies and Requirements

To run this reproducible pipeline, you must have the following dependencies installed:

- **R Version:** 4.0 or higher
- **IDE:** RStudio (Recommended)
- **R Packages:**
  - Data Manipulation & I/O: `arrow`, `tidyverse`
  - EDA & Visualisation: `skimr`, `corrplot`, `scales`, `gridExtra`
  - Machine Learning & Modeling: `caret`, `glmnet`, `randomForest`, `xgboost`, `lightgbm`, `caretEnsemble`
  - Evaluation & Metrics: `Metrics`, `vip`
  - Parallel Processing: `doParallel`

*(Note: The first chunk in the `.Rmd` file includes an auto-install script that will automatically download and install any missing packages from CRAN).*

---

##  Project Scope and Goals

**What was successfully reproduced:**
- **Exploratory Data Analysis (EDA):** Recreated all major visualisations and data insights (Target distribution, Geographic spread, Correlation heatmaps, etc.).
- **Machine Learning Modeling:** Successfully trained, evaluated, and compared several models predicting property prices (log1p scale). 
  - *Models used:* OLS, Ridge, ElasticNet, Random Forest, XGBoost, LightGBM, and a Stacking Ensemble.
  - *Outcome:* We managed to reproduce the same high-quality results and predictive performance as the original Python implementation.

**What was excluded (Out of Scope):**
- **Feature Engineering:** The original feature engineering pipeline was heavily reliant on specific Python spatial libraries and was excluded due to time constraints. We used the pre-processed data for our R modeling pipeline.
- **Deployment & MLOps:** The deployment components (FastAPI backend, Streamlit frontend, Docker containerisation, MLflow tracking, and GCP Cloud Run) were not translated to R.

---

##  Repository Structure

```text
MLOps-GCP-RR/
├── Data/               # Processed datasets (parquet format)
├── Notebooks/          
│   ├── dubai_houses_ml.Rmd   # Main R Markdown file containing the reproduced pipeline
│   ├── dubai_houses_ml.html  # Knitted HTML report of the Rmd file
│   └── models/               # Saved R models (.rds, .model, .txt)
└── README.md           # Project documentation (this file)
```

---

##  Getting Started

### Running the R Pipeline

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Mukhammadkodir27/MLOps-GCP-RR.git
   cd MLOps-GCP-RR
   ```

2. **Open the R Markdown file:**
   Open `Notebooks/dubai_houses_ml.Rmd` in RStudio.

3. **Install Dependencies:**
   Run the setup chunk in the notebook, which handles the `install.packages()` logic automatically.

4. **Knit the Document:**
   Click the **Knit** button in RStudio to run the entire pipeline and generate the HTML report, or run the chunks sequentially to explore the data and models interactively.
5. # R Environment Requirements for dubai_houses_ml.Rmd

## R Version

- **Minimum R version:** 3.6.0
- **Recommended R version:** 4.0.0 or higher (4.1.x, 4.2.x, 4.3.x)
- **Tested on:** R 4.1.x - 4.3.x

---

## R Package Dependencies & Versions

| Package | Minimum Version | Recommended | Purpose |
|---------|-----------------|------------|---------|
| **arrow** | 7.0.0 | ≥10.0.0 | Parquet file I/O |
| **tidyverse** | 1.3.0 | ≥1.3.2 | Data manipulation & ggplot2 |
| **dplyr** | 1.0.0 | ≥1.0.9 | Data wrangling (part of tidyverse) |
| **tidyr** | 1.1.0 | ≥1.2.0 | Data reshaping (part of tidyverse) |
| **ggplot2** | 3.3.0 | ≥3.4.0 | Visualization (part of tidyverse) |
| **skimr** | 2.1.0 | ≥2.1.4 | Data profiling |
| **corrplot** | 0.84 | ≥0.92 | Correlation matrix plots |
| **scales** | 1.1.0 | ≥1.2.0 | Axis scaling & labeling |
| **gridExtra** | 2.3 | ≥2.3 | Grid graphics arrangement |
| **caret** | 6.0-85 | ≥6.0-90 | ML framework & model training |
| **glmnet** | 4.0 | ≥4.1 | Ridge & Elastic Net (via caret) |
| **randomForest** | 4.6-14 | ≥4.7 | Random Forest |
| **xgboost** | 1.4.0 | ≥1.5.0 | XGBoost gradient boosting |
| **lightgbm** | 3.0.0 | ≥3.2.0 | LightGBM gradient boosting |
| **Metrics** | 0.1.4 | ≥0.1.4 | Performance metrics (mae, rmse) |
| **vip** | 0.2.0 | ≥0.3.0 | Variable importance plots |
| **caretEnsemble** | 2.0.0 | ≥2.0.0 | Stacking & ensemble methods |
| **doParallel** | 1.0.15 | ≥1.0.16 | Parallel computing |
| **foreach** | 1.5.0 | ≥1.5.1 | Looping with doParallel |

---

## Installation Instructions

### Option 1: Install from CRAN (Recommended)

```r
# Core packages
install.packages(c(
  "arrow", "tidyverse", "skimr", "corrplot", "scales",
  "gridExtra", "caret", "glmnet", "randomForest",
  "xgboost", "lightgbm", "Metrics", "vip",
  "caretEnsemble", "doParallel"
))
```

### Option 2: Install with Version Specifications

```r
# Install specific versions (if needed)
install.packages("arrow", version = "10.0.0")
install.packages("tidyverse", version = "1.3.2")
install.packages("caret", version = "6.0-93")
install.packages("xgboost", version = "1.7.0")
install.packages("lightgbm", version = "4.0.0")
```

### Option 3: Use renv for Reproducibility (Recommended for Long-term)

```r
# Create a lockfile
renv::init()

# Or capture current environment
renv::snapshot()

# To restore later
renv::restore()
```

---

## Verifying Installation

```r
# Check installed versions
packageVersion("arrow")
packageVersion("caret")
packageVersion("xgboost")
packageVersion("lightgbm")

# Or check all at once
pkgs <- c("arrow", "tidyverse", "skimr", "corrplot", "scales",
          "gridExtra", "caret", "glmnet", "randomForest",
          "xgboost", "lightgbm", "Metrics", "vip",
          "caretEnsemble", "doParallel")
sapply(pkgs, packageVersion)
```

---

## System Requirements

### Windows
- No additional requirements
- Visual C++ redistributables may be needed for some packages

### macOS
- Xcode Command Line Tools recommended
- Install via: `xcode-select --install`

### Linux (Ubuntu/Debian)
```bash
# Install R
sudo apt-get install r-base r-base-dev

# Install system dependencies for compiled packages
sudo apt-get install libcurl4-openssl-dev libssl-dev libxml2-dev
```

---

## Hardware Recommendations

- **RAM:** Minimum 8GB (16GB+ recommended for large datasets)
- **CPU:** Multi-core processor (4+ cores for parallel processing)
- **Disk Space:** 2GB free space for packages and data

---

## Known Compatibility Issues

| Issue | Solution |
|-------|----------|
| XGBoost/LightGBM compilation errors | Update Rtools (Windows) or build tools (macOS/Linux) |
| caret conflicts with newer tidyverse | Use `caret ≥6.0-90` and `tidyverse ≥1.3.1` |
| doParallel not working | Ensure `foreach` is also installed |
| Arrow Parquet errors | Update Arrow to ≥10.0.0 |

---

## Creating a Complete renv.lock File

If you want to save the exact environment, run:

```r
# In the directory with dubai_houses_ml.Rmd
renv::init()
renv::snapshot()  # Creates renv.lock

# Then others can restore it with:
renv::restore()
```

---

## Quick Setup Script

```r
# Copy this entire script to set up your environment

# 1. Install all packages
packages <- c(
  "arrow", "tidyverse", "skimr", "corrplot", "scales",
  "gridExtra", "caret", "glmnet", "randomForest",
  "xgboost", "lightgbm", "Metrics", "vip",
  "caretEnsemble", "doParallel"
)

missing_pkgs <- packages[!packages %in% installed.packages()[, "Package"]]
if (length(missing_pkgs) > 0) {
  install.packages(missing_pkgs, dependencies = TRUE, repos = "https://cloud.r-project.org")
}

# 2. Load all packages
suppressPackageStartupMessages({
  sapply(packages, library, character.only = TRUE)
})

# 3. Verify versions
cat("=== Package Versions ===\n")
sapply(packages, packageVersion)

cat("\nEnvironment ready for dubai_houses_ml.Rmd!\n")
```

Save this as `setup_environment.R` and run with:
```r
source("setup_environment.R")
```

