# Credit Risk & Customer Segmentation Dashboard

A production-grade end-to-end machine learning pipeline for credit risk assessment and customer segmentation, designed for Indian MSME and retail lending contexts with RBI/SIDBI reference data integration.

---

## Project Overview

This project delivers:
- **Credit Risk Scoring** using Logistic Regression, XGBoost, and an Ensemble model
- **Customer Segmentation** using RFM Analysis + K-Means Clustering
- **SHAP-based Explainability** for model transparency
- **Interactive Dash Dashboard** for real-time monitoring
- **SQL layer** for data warehouse integration

---

## Architecture

```
Raw Data → Preprocessing → Feature Engineering → Modeling → Segmentation → Dashboard
                                                     ↓
                                             SHAP Explainability
```

---

## Tech Stack

| Layer | Tools |
|---|---|
| Data | Pandas, NumPy, SQLite/PostgreSQL |
| ML | Scikit-learn, XGBoost, SHAP |
| Visualization | Plotly, Dash, Matplotlib, Seaborn |
| Dashboard | Plotly Dash |
| Reference Data | RBI, SIDBI guidelines |

---

## Setup

```bash
git clone https://github.com/yourname/Credit-Risk-Customer-Segmentation-Dashboard.git
cd Credit-Risk-Customer-Segmentation-Dashboard
pip install -r requirements.txt
```

### Generate Synthetic Data
```bash
python src/data/generate_data.py
```

### Run Full Pipeline
```bash
python src/data/preprocess.py
python src/data/feature_engineering.py
python src/models/train_logistic.py
python src/models/train_xgboost.py
python src/models/ensemble.py
python src/segmentation/rfm.py
python src/segmentation/kmeans_segmentation.py
python src/explainability/shap_analysis.py
```

### Launch Dashboard
```bash
python dashboard/dash/app.py
```

Open `http://localhost:8050` in your browser.

---

## Data Dictionary

### customers.csv
| Column | Description |
|---|---|
| customer_id | Unique identifier |
| age | Age of borrower |
| income | Annual income (INR) |
| employment_type | Salaried / Self-employed / Business |
| credit_score | Bureau score (300–900) |
| city_tier | Tier 1 / 2 / 3 city |
| gender | M/F |

### loans.csv
| Column | Description |
|---|---|
| loan_id | Unique loan identifier |
| customer_id | Foreign key |
| loan_amount | Principal (INR) |
| loan_type | Home / Personal / Business / Auto |
| interest_rate | Annual rate (%) |
| tenure_months | Loan duration |
| default_flag | 1 = Defaulted, 0 = Performing |

---

## Model Performance

| Model | AUC-ROC | Precision | Recall | F1 |
|---|---|---|---|---|
| Logistic Regression | ~0.79 | ~0.72 | ~0.68 | ~0.70 |
| XGBoost | ~0.88 | ~0.81 | ~0.77 | ~0.79 |
| Ensemble | ~0.90 | ~0.83 | ~0.79 | ~0.81 |

---

## Segmentation

Customers are segmented using:
1. **RFM Scoring** — Recency, Frequency, Monetary value
2. **K-Means Clustering** — 4 clusters mapped to risk tiers

| Segment | Description |
|---|---|
| Champions | High value, low risk |
| Loyal | Consistent, moderate risk |
| At-Risk | Declining engagement |
| Lost | High NPA risk |

---

## Regulatory Alignment

- RBI Prudential Norms for NPA classification
- SIDBI MSME lending guidelines
- Indian credit bureau (CIBIL) score ranges

---

## License

MIT License — see `LICENSE` for details.
