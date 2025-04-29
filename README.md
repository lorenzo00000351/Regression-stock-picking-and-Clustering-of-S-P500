# 📈 TEAM PROJECT: S&P 500 Financial Prediction and Clustering

![Built with Python](https://img.shields.io/badge/Built%20with-Python-3776AB?logo=python&logoColor=white)

**Contributors:**  
Laia Farrés • Alex Buixeda • Arnau Urbina • Lorenzo Longobardi

---

## Table of Contents
- [Introduction](#introduction)
- [Data Acquisition and Enrichment](#data-acquisition-and-enrichment)
- [Data Cleaning](#data-cleaning)
- [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)
- [Feature Engineering](#feature-engineering)
- [Prediction and Results](#prediction-and-results)
  - [Data Preparation](#data-preparation)
  - [Models Used](#models-used)
  - [Evaluation Metrics](#evaluation-metrics)
  - [Model Interpretability](#model-interpretability)
  - [Prediction Phase Conclusion](#prediction-phase-conclusion)
- [Clustering S&P 500 Companies](#clustering-sp-500-companies)
  - [Introduction](#clustering-introduction)
  - [Feature Selection](#feature-selection)
  - [Applying Clustering](#applying-clustering)
  - [Cluster Interpretation](#cluster-interpretation)
  - [Investment Strategy Based on Clusters](#investment-strategy-based-on-clusters)

---

## 📚 Introduction
In this project, we developed a model to predict the profitability of S&P 500 companies using regression techniques and clustering. We collected and cleaned financial data, experimented with various regression algorithms, and applied clustering techniques to group companies based on financial patterns. Finally, we evaluated the feasibility of deploying the model in real-world financial environments.

---

## 🗂️ Data Acquisition and Enrichment
- **APIs & Scraping:** 
  - **Alpha Vantage API**: Retrieved historical and fundamental financial data (2013–2023).
  - **Wikipedia Scraping**: Gathered tickers for S&P 500 companies.
- **Storage:** Structured in Pandas DataFrames for efficient access in subsequent stages.
- **Enrichment:** Added sector information via additional web scraping.

---

## 🧹 Data Cleaning
Main tasks performed:
- **Duplicate Removal:** Consolidated repeated entries.
- **Null Handling:** Imputation using forward-fill, backward-fill, statistical measures, and domain-specific logic.
- **Format Correction:** Ensured type consistency across variables.
- **Outlier Treatment:** Statistical methods and visualization for detection and mitigation.

---

## 📊 Exploratory Data Analysis (EDA)
- **Visualizations:** Histograms, box plots, and time series.
- **Correlation Analysis:** Identified relationships between key financial metrics.
- **Sectoral Insights:** Similar financial ratio behaviors were observed within sectors.

---

## 🛠️ Feature Engineering
Calculated KPIs to improve model predictive power:
- ROE, ROIC, Debt-to-Equity, P/E Ratio, Net Income Margin, P/S Ratio, Market Cap, and Yearly Return.

---

## 🔮 Prediction and Results

### 📋 Data Preparation
- **Training Period:** 2013–2022
- **Testing Period:** 2023
- **Target Variable:** Year-over-year return percentage.

```python
df['next_year_return'] = (df['next_year_end_price'] / df['Year-End Price']) - 1
```
- **Scaling:** StandardScaler applied.

---

### 🧠 Models Used
- Linear Regression (Baseline)
- Random Forest Regressor
- Gradient Boosting Regressor
- XGBoost Regressor
- CatBoost Regressor

---

### 📈 Evaluation Metrics
Primary metric: **Root Mean Squared Error (RMSE)**.

| Model                  | RMSE   |
|-------------------------|--------|
| Linear Regression       | 1281.24|
| Random Forest Regressor | 0.27   |
| Gradient Boosting       | 0.29   |
| XGBoost                 | 0.30   |
| CatBoost                | 0.28   |

Tree-based models significantly outperformed linear regression.

---

### 🧩 Model Interpretability
Using **SHAP values**:
- Key predictors: `Year`, `FED Interest Rate`, `Market Cap`, `Market Cap pct_change`, `Year-End Price pct_change`.
- SHAP plots provided detailed impact visualizations of each feature on individual predictions.

---

### ✅ Prediction Phase Conclusion
- **Strategy Performance:**  
  - Top 20 predicted companies achieved **+43.77%** return (vs **+14.67%** S&P 500 index return).
- **Conclusion:**  
  - Financial historical data enables reasonably accurate future profitability prediction.
  - Tree-based ensemble models (RandomForest, CatBoost) perform best.
  - Interpretability tools like SHAP align predictions with economic reasoning.

---

## 🧩 Clustering S&P 500 Companies

### 📋 Clustering Introduction
Segmented S&P 500 companies based on financial and market indicators to detect investment opportunities and risk profiles.

---

### 🔍 Feature Selection
Selected 9 financial indicators grouped into four pillars:
- **Profitability:** ROE, EBITDA Margin
- **Solvency & Liquidity:** Debt-to-Equity, Current Ratio, Free Cash Flow
- **Valuation:** P/E Ratio, P/S Ratio
- **Growth:** Sales Growth, Price Growth

---

### ⚙️ Applying Clustering
- **Optimal Clusters:** Determined **k = 6** using the Elbow method.
- **Algorithm:** K-Means clustering applied.

---

### 📈 Cluster Interpretation

- **Cluster 1:** High-growth, high-risk companies with strong profitability but elevated leverage.
- **Cluster 2:** Mature, stable companies with limited growth potential.
- **Cluster 3:** Operationally efficient but financially weak companies.
- **Cluster 4:** Undervalued companies with stable profitability; ideal for value investing.
- **Cluster 5:** Financially strong giants (e.g., likely "Magnificent 7").
- **Cluster 6:** Highly leveraged, volatile companies with substantial bankruptcy risk.

---

### 💡 Investment Strategy Based on Clusters
- **Cluster 4:** Suitable for **Value Investing** (low valuation, good fundamentals).
- **Cluster 1:** Suitable for **Growth Investing** (high expansion potential, higher risk).
- **Cluster 5:** Follows general market trends; stable, reliable investments.

> Investment choice should align with individual risk appetite and financial goals.

---

## 📂 Project Structure

```bash
├── 1_DataIngestion_AlphaVantage.ipynb
├── 2_DataEnrichment.ipynb
├── 3_DataCleaning.ipynb
├── 4_EDA.ipynb
├── 5_FeatureEngineering.ipynb
├── 6_Prediction_&_Results.ipynb
├── 7_Clustering.ipynb
```




