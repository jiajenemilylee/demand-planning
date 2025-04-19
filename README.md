
# 📘 Monthly Demand Forecasting for Strategic Supply Planning

## 🎯 Project Overview

This project builds a monthly-level demand forecasting model using historical SKU demand data from a global manufacturing company. The goal is to simulate the role of a **Supply Planner**, focusing on regional warehouse replenishment strategy, SKU-level allocation, and baseline forecast modeling.

Dataset source: [Kaggle - Product Demand Forecasting](https://www.kaggle.com/datasets/felixzhao/productdemandforecasting)

---

## 🗂️ Dataset Summary

| Column             | Description                                |
|--------------------|--------------------------------------------|
| `Product_Code`     | Unique identifier for product SKU          |
| `Warehouse`        | Warehouse code                             |
| `Product_Category` | Product category                           |
| `Date`             | The date customer needs the product        |
| `Order_Demand`     | Single order quantity                      |

- Date range: 2011–2016  
- Volume: 1 million+ rows  
- Granularity: Daily demand per SKU per warehouse

---

## 📌 Objective

1. Aggregate raw daily demand into **monthly-level time series** at SKU + warehouse granularity
2. Perform **EDA** and **seasonal decomposition** to detect patterns
3. Build a **rule-based additive model (trend + seasonality)** to forecast demand for Q1 2017
4. Visualize and interpret results to support replenishment decisions

---

## 📊 Exploratory Data Analysis (EDA)

- Top SKUs were identified based on total order volume
- SKU `Product_0083` at `Whse_S` was selected for modeling due to:
  - Clear **upward trend**
  - Stable **year-end seasonal peaks**
  - Low residual noise

![Trend Chart](./forecast_vs_actual.png)

---

## 🔍 Time Series Decomposition

Applied **additive seasonal decomposition** with a 12-month period using `statsmodels`.

| Component    | Observation                                                                 |
|--------------|-----------------------------------------------------------------------------|
| Trend        | Stable long-term upward growth (ideal for proactive planning)              |
| Seasonality  | Consistent Q4 peaks → Possible linkage with end-of-year promotional cycles |
| Residual     | Low residual variance → model is robust                                     |

---

## 📈 Forecasting Methodology

**Model used:**  
```python
Forecast = Latest Trend Value + Average Monthly Seasonality
```

**Forecast Output for Q1 2017:**

| Month     | Forecasted Demand |
|-----------|-------------------|
| 2017-01   | 4,080,859         |
| 2017-02   | 3,617,619         |
| 2017-03   | 3,752,411         |

---

## 📦 Use Case

As a Supply Planner at a global company like Apple, accurate demand signals are essential to ensure just-in-time inventory levels across regional warehouses.
I simulate this scenario using:

- Aggregated SKU-month-warehouse demand
- Exploratory demand trend analysis
- Seasonal decomposition modeling (Trend + Seasonal + Residual)
- Baseline forecasting (additive)

---

## 🧰 Tech Stack

- **Python**, **Pandas**, **Matplotlib**, **Statsmodels**
- Google Colab (for execution)
- GitHub (for portfolio hosting)

---

## 💡 Next Steps (Optional Extensions)

- Automate forecast updates per SKU/region using rolling windows
- Introduce ML (XGBoost / LSTM) for comparison
- Add safety stock buffer simulation using service-level targets
- Optimize allocations across multiple warehouses based on forecast output

---

## 🙋‍♀️ Author

Jia-Jen Lee  
Associate Product Manager, Supply Chain & Operations
[LinkedIn](https://www.linkedin.com/in/jiajenlee/) 
