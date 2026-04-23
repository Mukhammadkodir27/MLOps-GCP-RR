# 🏙️ Dubai Real Estate Price Prediction Platform
### Reproducible Research Project — End-to-End ML & Generative AI System

---

## 👥 Group Members

| Name | Role |
|------|------|
| Mukhammadkodir Abdusalomov | ML Pipeline & Feature Engineering |
| Elbek Majidov | Cloud Infrastructure & Deployment |
| Mirzakalonboy Khamidov | AI Chatbot & API Integration |

---

## Research Question

**Can we accurately predict residential property prices in Dubai using structured real estate transaction data, and can a generative AI layer translate these predictions into natural, human-readable insights for end users?**

Secondary questions:
- Which features (location, size, property type, floor, etc.) are the strongest predictors of Dubai land prices?
- How well does a stacked ensemble model outperform individual regression baselines?
- Can containerized cloud deployment (GCP + Kubernetes) make such a system production-ready and reproducible?

---

## Data Source

- **Source:** Dubai Land Department (DLD) — publicly available real estate transaction records
- **Coverage:** Historical property sales across Dubai's major districts
- **Key Features:** Property type, area (sq ft), location/district, number of bedrooms, floor level, transaction date, price per sq ft, and total transaction value
- **Size:** Large-scale tabular dataset with high-dimensional categorical and numerical features

---

## Motivation

Dubai's real estate market is one of the most dynamic and opaque property markets globally, with prices varying dramatically across neighborhoods, property types, and even building floors. Buyers, investors, and analysts often lack accessible tools to estimate fair market value without expert consultation.

This project tackles that gap by building a high-precision ML regression system backed by a conversational AI interface — making price predictions accessible to non-technical users through natural language. By migrating from Azure to **Google Cloud Platform with Kubernetes**, we also explore how containerized, orchestrated deployments improve reproducibility, scalability, and collaboration in applied ML research.

---

## Planned Approach

### 1. Data Preparation
- Data cleaning, type normalization, and missing value treatment
- Outlier detection using statistical and model-based methods (IQR, Isolation Forest)
- Advanced feature engineering: price-per-sqft ratios, district-level aggregations, temporal features from transaction dates

### 2. Modeling
- Baseline models: Linear Regression, Ridge, Lasso, Decision Tree
- Advanced models: XGBoost, LightGBM, Random Forest
- **Final model: Stacked Ensemble** — combining base learners with a meta-regressor for higher precision
- Evaluation metrics: RMSE, MAE, R²

### 3. Generative AI Layer
- Integration of **Gemini API** as a conversational chatbot layer
- Zero/few-shot prompt engineering for reliable, injection-safe responses
- Natural language input → structured prediction → human-readable output

### 4. Deployment (GCP + Kubernetes)
- Containerize the ML pipeline and FastAPI backend using **Docker**
- Deploy and orchestrate containers on **Google Kubernetes Engine (GKE)**
- Expose endpoints via a scalable, managed cloud infrastructure
- Environment and dependency management for full reproducibility

### 5. Collaboration & Reproducibility
- Version control via **Git** with **GitKraken** for visual branch management
- Reproducible training pipeline with fixed random seeds and logged hyperparameters
- Environment pinned via `requirements.txt` / `environment.yml`

---

## Language & Tools

| Category | Tools |
|----------|-------|
| **Language** | Python 3.10+ |
| **ML & Data** | scikit-learn, XGBoost, LightGBM, pandas, NumPy |
| **API & Backend** | FastAPI |
| **Generative AI** | Google Gemini API |
| **Cloud** | Google Cloud Platform (GCP) |
| **Orchestration** | Google Kubernetes Engine (GKE) |
| **Containerization** | Docker |
| **Collaboration** | Git, GitKraken |
| **Experiment Tracking** | MLflow *(planned)* |
| **Notebook Environment** | Jupyter Notebook / VS Code |

---

## System Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│  Dubai Real Estate Data (DLD)                                    │
│         │                                                        │
│         ▼                                                        │
│  [Data Preprocessing & Feature Engineering]                      │
│   Outlier Detection · Encoding · Aggregations                    │
│         │                                                        │
│         ▼                                                        │
│  [Stacked Ensemble Regression Engine]                            │
│   XGBoost · LightGBM · RF → Meta-Regressor                       │
│         │                                                        │
│         ▼                                                        │
│  [FastAPI Backend]  ──►  Dockerized Container                    │
│         │                                                        │
│         ▼                                                        │
│  [Google Kubernetes Engine (GKE)]                                │
│   Scalable · Managed · Reproducible                              │
│         │                                                        │
│         ▼                                                        │
│  [Gemini API Chatbot Layer]                                      │
│   Zero/Few-Shot Prompting · Natural Language Predictions         │
└──────────────────────────────────────────────────────────────────┘
```

---

## 📁 Repository Structure *(planned)*

```
dubai-realestate-prediction/
├── data/                  # Raw and processed datasets
├── notebooks/             # EDA and experimentation notebooks
├── src/
│   ├── preprocessing/     # Feature engineering & cleaning scripts
│   ├── models/            # Training, stacking, evaluation
│   └── api/               # FastAPI app + Gemini chatbot
├── docker/                # Dockerfile and docker-compose
├── k8s/                   # Kubernetes manifests (GKE)
├── requirements.txt
├── environment.yml
└── README.md
```

---

## Reproducibility

To reproduce this project:

```bash
# Clone the repository
git clone https://github.com/your-org/dubai-realestate-prediction.git
cd dubai-realestate-prediction

# Install dependencies
pip install -r requirements.txt

# Run the training pipeline
python src/models/train.py

# Launch the API locally
uvicorn src.api.main:app --reload

# Or run via Docker
docker build -t dubai-ml .
docker run -p 8000:8000 dubai-ml
```

> Full GKE deployment instructions will be documented in `/k8s/README.md`

---

## Status

- [x] Initial ML pipeline (Azure — previous version)
- [x] Stacked ensemble model with feature engineering
- [ ] Migration to GCP + Docker + Kubernetes
- [ ] Gemini API chatbot integration
- [ ] Full reproducibility documentation
- [ ] Final evaluation and results write-up
