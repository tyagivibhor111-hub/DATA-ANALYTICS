# Customer Segmentation & Sales Analytics for an Online Retail Business

A medium-difficulty data analytics project that cleans e-commerce transaction data, explores sales
trends, engineers RFM (Recency, Frequency, Monetary) features, segments customers with K-Means
clustering, and produces a simple short-term revenue forecast.

## Project Description

Online retailers sit on transaction logs that, with the right analysis, reveal *when* customers
buy, *what* drives revenue, and *which* customers are most valuable or at risk of churning. This
project builds an end-to-end analytics pipeline that answers those questions:

1. **Data cleaning** — parse dates, remove cancelled orders and invalid rows, handle missing
   customer IDs, and compute per-line revenue.
2. **Exploratory Data Analysis (EDA)** — monthly revenue trend, top products, top countries,
   order-value distribution, and revenue by day of week.
3. **RFM feature engineering** — Recency, Frequency, and Monetary value per customer.
4. **Customer segmentation** — K-Means clustering on standardized RFM features, with the number
   of clusters chosen via the elbow method and silhouette score, followed by business-friendly
   segment labels (e.g., "Champions", "At Risk").
5. **Revenue forecasting** — a linear trend + monthly-seasonality model projecting the next 3
   months of revenue, validated on a hold-out period.
6. **Insights & recommendations** — concrete, business-facing takeaways from the analysis.

## Dataset

The notebook is built around the schema of the well-known **UCI "Online Retail II"** dataset
(invoice-level transactions from a UK-based online gift retailer, 2009–2011):

- Dataset page: https://archive.ics.uci.edu/dataset/502/online+retail+ii
- Kaggle mirror: https://www.kaggle.com/datasets/mashlyn/online-retail-ii-uci

**To use the real dataset:** download `online_retail.csv` from either link above (CSV export) and
place it in the same folder as the notebook before running it.

**Default behavior:** if `online_retail.csv` is not found, the notebook automatically **generates a
realistic synthetic dataset** with the same columns, seasonality patterns, and a Pareto-like spend
distribution across customers, so the entire pipeline runs end-to-end out of the box without any
internet access or manual download. The generated file is also saved locally as `online_retail.csv`
on first run.

Columns: `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`,
`CustomerID`, `Country`.

## Technologies Used

- **Python 3**
- **pandas / numpy** — data manipulation
- **matplotlib / seaborn** — visualization
- **scikit-learn** — `StandardScaler`, `KMeans`, `silhouette_score`, `LinearRegression`
- **Jupyter Notebook**

## Setup & Run Instructions

1. **Clone/download this project folder** so `VibhuTyagi_CustomerSegmentationSalesAnalytics.ipynb`
   and (optionally) `online_retail.csv` are in the same directory.
2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   source venv/bin/activate   # Windows: venv\Scripts\activate
   ```
3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
4. **(Optional) Add the real dataset:** place `online_retail.csv` (from the links above) in the
   project folder. If skipped, the notebook generates synthetic data automatically.
5. **Launch Jupyter and run the notebook top to bottom:**
   ```bash
   jupyter notebook VibhuTyagi_CustomerSegmentationSalesAnalytics.ipynb
   ```
   Then: **Kernel → Restart & Run All**.

## Project Structure

```
├── VibhuTyagi_CustomerSegmentationSalesAnalytics.ipynb   # Main analysis notebook
├── requirements.txt                                       # Python dependencies
├── LICENSE                                                 # Full written report
└── README.md                                              # This file
```

## Key Outputs

- Monthly revenue trend chart with clear seasonal (Q4) uplift
- Top 10 products and top 10 countries by revenue
- RFM distributions and a Recency-vs-Monetary customer segmentation scatter plot
- Elbow/silhouette plots justifying the chosen number of customer segments
- A labeled cluster profile table (e.g., Champions, At Risk, Potential Loyalists, New/Low-Engagement)
- A 3-month revenue forecast plotted against actuals

## Notes

- Random seed is fixed (`RANDOM_SEED = 42`) so synthetic-data results are reproducible run to run.
- All numeric findings quoted in the accompanying report were generated from a run of this
  notebook and will regenerate consistently if re-run with the same seed and library versions.
