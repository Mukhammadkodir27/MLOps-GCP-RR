# 🇦🇪 UAE Property Valuator - R Reproducibility Project

![R](https://img.shields.io/badge/R-4.0+-276DC3?logo=r&logoColor=white)
![RStudio](https://img.shields.io/badge/RStudio-IDE-75AADB?logo=rstudio&logoColor=white)

This project is a reproduction of the UAE Property Valuator machine learning pipeline. The original project was built using Python (Jupyter Notebooks) as an end-to-end MLOps pipeline. As part of a reproducible research initiative, we successfully recreated the exploratory data analysis (EDA) and machine learning modeling stages entirely in **R**.

---

##  Project Scope and Goals

The primary goal was to validate the reproducibility of the original Python-based ML results using the R programming ecosystem. 

**What was successfully reproduced:**
- **Exploratory Data Analysis (EDA):** Recreated all major visualisations and data insights (Target distribution, Geographic spread, Correlation heatmaps, etc.) using `ggplot2`, `corrplot`, and `skimr`.
- **Machine Learning Modeling:** Successfully trained, evaluated, and compared several models predicting property prices (log1p scale). 
  - *Models used:* OLS, Ridge, ElasticNet, Random Forest, XGBoost, LightGBM, and a Stacking Ensemble (via `caretEnsemble`).
  - *Outcome:* We managed to reproduce the same high-quality results and predictive performance as the original Python implementation.

**What was excluded (Out of Scope):**
- **Feature Engineering:** The original feature engineering pipeline was heavily reliant on specific Python libraries and was excluded due to time constraints. We used the pre-processed data for our R modeling pipeline.
- **Deployment & MLOps:** The deployment components (FastAPI backend, Streamlit frontend, Docker containerisation, MLflow tracking, and GCP Cloud Run) were not translated to R, as they were beyond the scope of this reproducibility exercise.

---

##  Repository Structure

The key files for this R reproduction can be found in the `Notebooks` directory:

```text
Google-MLOps-UAE/
├── Data/               # Processed datasets (parquet format)
├── Notebooks/          
│   ├── dubai_houses_ml.Rmd   # The main R Markdown file containing the reproduced pipeline
│   ├── dubai_houses_ml.html  # The knitted HTML report of the Rmd file
│   └── models/               # Saved R models (.rds, .model, .txt)
└── README.md           # Project documentation (this file)
```

*(Note: The original Python files, Docker configurations, and Front-End code remain in the repository for reference but are not part of the R reproduction workflow).*

---

##  Getting Started

### Prerequisites
- R (version 4.0 or higher recommended)
- RStudio (optional, but recommended for viewing and running the `.Rmd` file)

### Running the R Pipeline

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Mukhammadkodir27/Google-MLOps-Reg-UAE.git
   cd Google-MLOps-Reg-UAE
   ```

2. **Open the R Markdown file:**
   Open `Notebooks/dubai_houses_ml.Rmd` in RStudio.

3. **Install Dependencies:**
   The `.Rmd` file includes an auto-install script in the first code chunk that will install all required packages (e.g., `tidyverse`, `caret`, `xgboost`, `lightgbm`, `arrow`).

4. **Knit the Document:**
   Click the **Knit** button in RStudio to run the entire pipeline and generate the HTML report, or run the chunks sequentially to explore the data and models interactively.

---

##  Machine Learning Pipeline in R

The reproduced pipeline follows these steps:
1. **Data Loading:** Reads pre-processed `.parquet` files using the `arrow` package.
2. **EDA:** Comprehensive visualizations mimicking the original notebook's insights.
3. **Cross-Validation Setup:** Parallelized cross-validation using `caret` and `doParallel` to speed up training.
4. **Model Training:** Training baseline models (LM, Ridge, ElasticNet), intermediate models (Random Forest), and advanced Gradient Boosting models (XGBoost, LightGBM).
5. **Stacking Ensemble:** Combining predictions using `caretEnsemble` for a robust final model.
6. **Evaluation:** Comparing models based on MAE, RMSE, and R² on both log-scale and the original AED scale.

---

##  Acknowledgements

This reproducibility project was developed for educational purposes to demonstrate cross-language ML pipeline recreation. The original Python architecture and this R reproduction both showcase the robustness of modern open-source data science tools.
