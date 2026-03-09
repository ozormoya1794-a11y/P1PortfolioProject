# Facebook Page Performance — Data Analytics Portfolio

**Author:** Ozor Moya 
**Date:** 08/08/2026

---

## About This Project

This project analyses 500 Facebook posts from a brand page to understand what drives engagement and builds regression models to predict total interactions.

---

## Project Structure

```
EOP-Projeect/P1PortfolioProject
│
├── Code/
│   ├── 01_explore.ipynb     ← Step 1: EDA and Data Wrangling
│   ├── 02_transform.ipynb   ← Step 2: Feature Engineering
│   └── 03_model.ipynb       ← Step 3: Linear, Ridge & Lasso Regression
│
├── Data/
│   ├── raw_dataset_Facebook.csv   ← Original file (never modified)
│   ├── cleaned_facebook.csv       ← Output of explore.ipynb
│   └── model_ready.csv            ← Output of transform.ipynb
│
├── Docs/
│   └── fig_*.png                  ← Charts saved by notebooks
│
└── README.md
```

---

## Dataset

| Property | Value |
|----------|-------|
| Source | UCI Machine Learning Repository |
| Records | 500 Facebook posts |
| Columns | 19 (renamed to snake_case) |
| Target | `Total Interactions` (comments + likes + shares) |
| File format | CSV with semicolon separator |

---

## What Each Notebook Does

### `explore.ipynb` — EDA & Data Wrangling
- Loads the semicolon-separated CSV
- Explains all 19 column names with a reference table
- Renames columns to short `snake_case` format
- Checks and fixes 6 missing values
- Explores distributions, timing patterns, and relationships
- Identifies skewed target variable and explains log transformation need

### `transform.ipynb` — Feature Engineering
- One-hot encodes `post_type` (Photo/Status/Link/Video)
- Creates `engagement_rate` and `is_weekend` features
- Applies log transform to target variable
- Removes data leakage columns (`comments`, `likes`, `shares`)
- Saves model-ready dataset

### `model.ipynb` — Regression Models
- Splits data 80% train / 20% test
- Scales features with StandardScaler
- Trains and compares three models:
  - Linear Regression (baseline)
  - Ridge Regression (handles correlated features)
  - Lasso Regression (automatic feature selection)
- Evaluates with R², MAE, RMSE, and 5-fold CV
- Plots actual vs predicted and feature coefficients

---

## Key Findings

- 85% of posts are Photos, but Status posts get higher median engagement
- 28% of posts were paid — paid posts have more interactions mainly via reach
- `total_interactions` is heavily skewed — log transformation applied for modeling
- `engaged_users` and `total_reach` are the strongest predictors


---

## Tech Stack

- Python 3
- pandas, numpy
- matplotlib, seaborn
- scikit-learn
- Jupyter Notebook

---

## Data Source

Moro, S., Rita, P., & Vala, B. (2016). *Predicting social media performance metrics.*  
[UCI ML Repository — Facebook Metrics Dataset](https://archive.ics.uci.edu/ml/datasets/Facebook+metrics)
