
# SKU Demand Forecasting for Strategic Supply Planning

## 🎯 Project Overview

This project simulates the role of a **Supply Planner** at a global tech company by building a SKU-level, warehouse-specific monthly demand forecasting model. Using historical order data, the project focuses on trend discovery, seasonality analysis, and rule-based forecasting to guide replenishment planning.

**Data source:** [Kaggle - Product Demand Forecasting](https://www.kaggle.com/datasets/felixzhao/productdemandforecasting)  
**Tools used:** Python, Pandas, Statsmodels, Matplotlib (Google Colab)

**Full explanation and business insights available on Medium:**  
🔗 [Read the full analysis here](https://medium.com/@jiajenlee/sku-level-demand-forecasting-for-strategic-supply-planning-83f7eeb5f847)

---

## 🗂️ Dataset Description

| Column             | Description                                  |
|--------------------|----------------------------------------------|
| `Product_Code`     | Unique identifier for each SKU               |
| `Warehouse`        | Warehouse location code                      |
| `Product_Category` | Product category name                        |
| `Date`             | Date of customer need                        |
| `Order_Demand`     | Order quantity (daily granularity)           |

- **Time span:** 2011–2016  
- **Volume:** 1M+ rows  
- **Granularity:** Daily demand per SKU per warehouse  

---

## 📌 Project Goals

1. **Aggregate** raw demand to monthly time series by SKU + warehouse
2. **Identify trends and seasonality** through visual and statistical EDA
3. **Build baseline forecasts** using additive models (trend + seasonality)
4. **Support replenishment planning** for Q1 2017 using forecast outputs

---

## 📊 EDA Insights

- Top SKUs were ranked by total historical demand  
- Three focus combinations were selected for modeling:
  - `Product_1359` @ `Whse_J`
  - `Product_1248` @ `Whse_J`
  - `Product_0083` @ `Whse_S` (strong seasonal signal)

Common traits observed:
- Stable trend trajectories
- Distinct Q3–Q4 seasonality in multiple SKUs
- Low residual noise → ideal for baseline forecasting

---

## 🔍 Time Series Decomposition

Additive decomposition (12-month cycle) was applied to isolate:
- **Trend** — reveals long-term directionality
- **Seasonal** — highlights cyclical patterns
- **Residual** — captures random fluctuation / noise

Example:  
![Trend Chart](./forecast_vs_actual.png)

---

## 📈 Forecasting Method

We used a **rule-based additive model** without ML:

```python
Forecast_t = Trend_latest + Seasonality_month(t)
```

This approach is useful when:
- Data is clean and shows strong repeatable patterns
- Forecasting latency or interpretability matters
- The business requires a stable baseline for inventory alignment

**Q1 2017 Forecast Sample:**

| Month   | Forecast Demand (Product_0083 @ Whse_S) |
|---------|-----------------------------------------|
| Jan     | 4,080,859                               |
| Feb     | 3,617,619                               |
| Mar     | 3,752,411                               |

---

## 🧠 Business Application

As a Supply Planner, this type of demand modeling enables:
- **Early identification of surge windows** for proactive purchasing
- **Dynamic warehouse-level safety stock** adjustment
- **Baseline forecast creation** before applying ML models

This project demonstrates:
- Data aggregation from transactional to planning level
- Seasonality analysis to support allocation strategies
- Scalable rule-based forecasting for SKU-region planning

---

## 🧰 Tech Stack

- Python + Pandas (data processing)
- Statsmodels (time series decomposition)
- Matplotlib (visualization)
- Google Colab (execution)
- GitHub (documentation & sharing)

---

## 🔁 Future Improvements

- Automate rolling-window trend & seasonal updates
- Integrate machine learning (XGBoost, Prophet, or LSTM)
- Simulate reorder points with safety stock buffers
- Multi-warehouse inventory pooling optimization

---

## 🙋‍♀️ Author

**Jia-Jen Lee**  
Associate Product Manager – Hardware Supply Chain & Operations  
[🔗 LinkedIn]([https://www.linkedin.com/in/jiajenlee/](https://www.linkedin.com/in/jia-jen-lee/))
