# 🇦🇪 UAE Real Estate Price Prediction Platform

**Live App:** https://mukhammadkodir-real-estate.streamlit.app/

> **Reproducible Research Project** — This project reproduces an existing Python-based ML pipeline for Dubai property price prediction, re-implementing the modeling and analysis in **R**. The original project was built in Python; this version converts the workflow to R, with feature engineering done in R where possible, or using preprocessed data as input to the R modeling pipeline.

---

## 👥 Group Members

| Name | Role |
|------|------|
| Mukhammadkodir Abdusalomov | ML Pipeline & Feature Engineering |
| Elbek Majidov | Cloud Infrastructure & Deployment |
| Mirzakalonboy Khamidov | AI Chatbot & API Integration |

---

## Research Question

Can we accurately predict residential property prices in Dubai using structured real estate transaction data — and can a generative AI layer translate these predictions into natural, human-readable insights?

**Secondary questions:**
- Which features (location, size, property type, floor, etc.) are the strongest predictors of price?
- How well does a stacked ensemble model outperform individual regression baselines?
- Can the original Python pipeline be faithfully reproduced in R?

---

## Original Project & Language Conversion

| | Original | This Reproduction |
|---|---|---|
| **Language** | Python 3.10+ | R |
| **ML Libraries** | scikit-learn, XGBoost, LightGBM | caret / tidymodels, xgboost, lightgbm |
| **Data Wrangling** | pandas, NumPy | dplyr, tidyr |
| **API / Backend** | FastAPI | (same or adapted) |
| **Generative AI** | Google Gemini API | Google Gemini API |

Feature engineering is reproduced in R where feasible. If a preprocessing step is not directly translatable, we use the processed dataset from the original pipeline as input to the R modeling stage.

---

## Data Source

- **Source:** Dubai Land Department (DLD) — publicly available transaction records
- **Key Features:** Property type, area (sq ft), district, bedrooms, floor, transaction date, price per sq ft, total price
- **Scale:** Large tabular dataset with high-dimensional categorical and numerical features

---

## Approach

**1. Data Preparation (R)**
- Cleaning, type normalization, missing value treatment
- Outlier detection (IQR-based and model-based)
- Feature engineering: price-per-sqft ratios, district aggregations, temporal features

**2. Modeling (R)**
- Baselines: Linear Regression, Ridge, Lasso, Decision Tree
- Advanced: XGBoost, LightGBM, Random Forest
- Final: Stacked Ensemble with a meta-regressor
- Metrics: RMSE, MAE, R²

**3. Generative AI Layer**
- Gemini API chatbot for natural language predictions
- Zero/few-shot prompting for safe, reliable responses

**4. Deployment**
- Dockerized FastAPI backend
- Google Kubernetes Engine (GKE) for scalable deployment

---

## Tools & Stack

| Category | Tools |
|----------|-------|
| **Reproduction Language** | R |
| **R Packages** | tidymodels, caret, xgboost, lightgbm, dplyr, ggplot2 |
| **Original Language** | Python 3.10+ |
| **Generative AI** | Google Gemini API |
| **Backend** | FastAPI |
| **Cloud / Deployment** | GCP, Docker, Kubernetes (GKE) |
| **Version Control** | Git, GitKraken |

---

## Repository Structure

```
dubai-realestate-prediction/
├── data/                  # Raw and processed datasets
├── notebooks/             # EDA (R Markdown / Jupyter)
├── R/                     # R scripts: preprocessing, modeling, evaluation
├── src/
│   ├── preprocessing/     # Original Python preprocessing (reference)
│   └── api/               # FastAPI + Gemini chatbot
├── docker/
├── k8s/
├── requirements.txt       # Python dependencies
├── renv.lock              # R environment lockfile
└── README.md
```

---

## Reproducing This Project

```bash
# Clone the repository
git clone https://github.com/your-org/dubai-realestate-prediction.git
cd dubai-realestate-prediction

# R environment
Rscript -e "renv::restore()"

# Run the R modeling pipeline
Rscript R/train_model.R

# Python backend (optional)
pip install -r requirements.txt
uvicorn src.api.main:app --reload

# Or run via Docker
docker build -t dubai-ml .
docker run -p 8000:8000 dubai-ml
```

---

## Status

- [x] Original Python ML pipeline (reference implementation)
- [ ] Stacked ensemble model with feature engineering (Python)
- [ ] R reproduction of feature engineering and modeling
- [ ] Gemini API chatbot integration
- [ ] GCP + Docker + Kubernetes deployment
- [ ] Final evaluation and comparison of Python vs R results
