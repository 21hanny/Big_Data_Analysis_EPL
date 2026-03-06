# Big_Data_Analysis_EPL

⚽ EPL Match Analytics — 2000 to 2025

> *25 seasons. 9,380 matches. One question: what actually wins football games?*

---

## 🏟️ Overview

A full data science pipeline applied to English Premier League match data spanning 25 seasons (2000–2025). The project moves from raw messy data through cleaning, feature engineering, exploratory analysis, and machine learning — with a focus on two research questions that matter to anyone who loves football.

**Dataset:** [EPL Match Data 2000–2025 — Kaggle](https://www.kaggle.com/datasets/marcohuiii/english-premier-league-epl-match-data-2000-2025)  
**Matches:** ~9,380 | **Seasons:** 25 | **Teams:** 49 clubs

---

## ❓ Research Questions

### 1. Can match KPIs predict full-time results?
> Shots, fouls, cards, corners — which of these actually decide who wins?  
> Built a Random Forest classifier + Logistic Regression to find out.

### 2. Which in-game metrics most influence outcomes?
> Used correlation analysis and logistic regression coefficients to rank the predictive power of every stat in the dataset.

---

## 🔬 What's Inside

### 🧹 Data Pipeline (`complete_epl_data_preparation_pipeline`)
A fully modular, documented cleaning pipeline:

| Step | Function | What it does |
|------|----------|-------------|
| 1 | `load_and_inspect_data()` | Load CSV, parse dates, initial inspection |
| 2 | `initial_clean_data()` | Drop nulls, fix types, remove duplicates |
| 3 | `comprehensive_data_quality_assessment()` | Missing values, type audit, logic checks |
| 4 | `detect_and_handle_outliers()` | IQR capping on all numeric columns |
| 5 | `advanced_missing_value_treatment()` | Team-based median imputation for corners, global median for others |
| 6 | `comprehensive_feature_engineering()` | 15+ new features derived from raw stats |
| 7 | `comprehensive_data_validation()` | Row count, consistency checks, quality score |

### ⚙️ Feature Engineering
New features created from raw match data:

- **Temporal:** Year, Month, Weekday, Season label
- **Result:** Win/Draw/Loss, Goal Difference, Total Goals
- **Efficiency:** Shot Accuracy, Conversion Rate (home & away)
- **Advanced:** Match Competitiveness Index, Excitement Index, Expected Goals (xG proxy)
- **Flags:** High Scoring Game (>5 goals), Very Physical Game (≥8 cards)

---

## 📊 Analyses & Visualisations

| Analysis | Key Finding |
|----------|-------------|
| **Match Distribution by Weekday** | Saturday dominates; Wednesday midweek fixture congestion visible |
| **Total Goals per Season** | Upward trend post-2010, dip around 2020 (COVID ghost games) |
| **Match Outcome Distribution** | Home wins historically most frequent — but is that changing? |
| **Home Advantage: Pre vs Post 2020** | COVID empty stadiums measurably reduced home win rate |
| **Top 3 Teams by Finishing Efficiency** | Clinical conversion matters more than raw shot volume |
| **Team Consistency vs League Success** | Lower points variance → higher final position (r ≈ 0.4+) |
| **Correlation Heatmap** | Shots on target strongest predictor; red cards weakly correlated |
| **Win Rate Scatter (2D + 3D)** | Home and away win rates together predict overall dominance |

---

## 🤖 Machine Learning

### Random Forest Classifier
- **Features:** HomeShots, AwayShots, ShotsOnTarget, Fouls, Corners, Cards
- **Target:** Full-time result (H / D / A)
- **Interactive widget** — pick any two teams, get a predicted outcome with probabilities

### Logistic Regression (Feature Importance)
- Multinomial logistic regression coefficients per class
- Reveals which stats push toward Home Win vs Draw vs Away Win
- Evaluated with accuracy, F1-score, classification report

---

## 🗂️ Files

```
📁 project/
├── PL_project.ipynb              # Main analysis notebook
├── dataset.csv                   # Raw EPL match data (2000–2025)
└── epl_cleaned_full_pipeline.csv # Cleaned & feature-engineered output
```

---

## 🚀 Getting Started

```bash
pip install pandas numpy matplotlib seaborn scikit-learn ipywidgets
```

Open `PL_project.ipynb` and run top to bottom — all data is local, no downloads needed.

> **Tip:** The interactive match predictor widget works best in **Jupyter Notebook** or **JupyterLab** (not VS Code's notebook viewer).

---

