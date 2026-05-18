# 📈 S&P 500 Stock Market Analysis Dashboard

> **A comprehensive end-to-end data analysis project** covering 16 years of S&P 500 top stock data (2010–2026) — from raw data cleaning and feature engineering in Python to interactive Power BI dashboards.

---

## 🗂️ Table of Contents

- [Project Overview](#-project-overview)
- [Dashboard Preview](#-dashboard-preview)
- [Key Insights](#-key-insights)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Dataset](#-dataset)
- [Analysis Workflow](#-analysis-workflow)
- [Power BI Dashboard](#-power-bi-dashboard)
- [How to Run](#-how-to-run)
- [Results Summary](#-results-summary)

---

## 🔍 Project Overview

This project performs a **full-stack financial data analysis** on the top 10 S&P 500 stocks across 16 years (January 2010 – February 2026). It combines **Python-based EDA and feature engineering** with a **3-page interactive Power BI dashboard** to uncover performance trends, risk profiles, and trading behavior.

**Stocks Analyzed:** `AAPL` · `AMZN` · `AVGO` · `GOOG` · `GOOGL` · `META` · `MSFT` · `NVDA` · `TSLA`

**Core Objectives:**
- Analyze long-term price performance and growth trends
- Engineer financial metrics: Daily Return, Moving Averages, Volatility
- Compare risk-return profiles across top S&P 500 components
- Build a professional, interactive multi-page Power BI dashboard

---

## 📊 Dashboard Preview

### 🏠 Executive Dashboard — Home
![Executive Dashboard](screenshots/page1_executive_dashboard.png)

*KPI cards showing $92.60 Average Close · 4.30T Total Volume · 3.17% Average Return · 184.24% Volatility. Includes stock price trend (2010–2026) and trading volume by ticker.*

---

### 📉 Performance Analysis
![Performance Analysis](screenshots/page2_performance_analysis.png)

*Total growth % comparison, average daily return by ticker, close price vs 30-day moving average, and daily return trend over time.*

---

### ⚠️ Risk Analysis
![Risk Analysis](screenshots/page3_risk_analysis.png)

*Volatility rankings, risk vs return scatter plot, return distribution (min/avg/max), and a color-coded risk classification table.*

---

## 💡 Key Insights

| Metric | Finding |
|--------|---------|
| 🏆 Highest Growth | **NVDA** — 26.2% total growth (2010–2026) |
| 📈 Best Daily Return | **NVDA** — avg 0.050% per day |
| ⚠️ Highest Risk | **TSLA** — volatility of 2.96 (classified: High) |
| 🛡️ Lowest Risk | **MSFT** — volatility of 1.25 (classified: Low) |
| 📦 Highest Volume | **NVDA** — 1.94T total shares traded |
| 💰 Highest Avg Price | **META** — avg close of $223.52 |
| 🔗 Strong Correlation | MSFT ↔ AAPL move closely together |
| 🆓 Most Independent | TSLA behaves differently from the broader group |

---

## 🛠️ Tech Stack

| Layer | Tools |
|-------|-------|
| **Data Analysis** | Python 3, Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn, Plotly Express |
| **Dashboard** | Power BI Desktop |
| **Notebook** | Jupyter Notebook / Google Colab |
| **Data Format** | CSV |

---

## 📁 Project Structure

```
sp500-stock-analysis/
│
├── data/
│   ├── sp500_top10_stocks_clean.csv       # Raw dataset (10 tickers, 2010–2026)
│   └── cleaned_stock_data.csv             # Feature-engineered dataset
│
├── notebooks/
│   └── S_P_500_Top_Stocks.ipynb           # Full Python analysis notebook
│
├── dashboard/
│   ├── S_P_500_Stock_Analysis_Dashboard.pbix   # Power BI file
│   ├── S_P_500_Stock_Analysis_Dashboard.pdf    # Static PDF export
│   └── sp500_dashboard.html                    # HTML export
│
├── screenshots/
│   ├── page1_executive_dashboard.png
│   ├── page2_performance_analysis.png
│   └── page3_risk_analysis.png
│
├── docs/
│   └── SP500_Project_Documentation.docx   # Full project documentation
│
└── README.md
```

---

## 📂 Dataset

| Field | Details |
|-------|---------|
| **Source** | Yahoo Finance (via yfinance / manual export) |
| **Period** | January 4, 2010 – February 13, 2026 |
| **Tickers** | 9 stocks (AAPL, AMZN, AVGO, GOOG, GOOGL, META, MSFT, NVDA, TSLA) |
| **Columns** | Date, Ticker, Open, High, Low, Close, Adj_Close, Volume |
| **Engineered** | Daily_Return, Price_Change, MA30, Volatility |

---

## 🔬 Analysis Workflow

The Jupyter notebook covers **6 structured phases:**

```
1. Import Libraries          →  pandas, numpy, matplotlib, seaborn, plotly
2. Understand the Dataset    →  shape, dtypes, info, statistical summary
3. Data Cleaning             →  date parsing, null checks, duplicate removal
4. Exploratory Data Analysis →  unique companies, date range, records per ticker
5. Feature Engineering       →  Daily Return · Price Change · MA30 · Volatility
6. Visualization             →  price trends, volume analysis, correlation heatmap
```

**Key engineered features:**

```python
# Daily Return — % gain/loss per trading day
df['Daily_Return'] = ((df['Close'] - df['Open']) / df['Open']) * 100

# 30-Day Moving Average
df['MA30'] = df.groupby('Ticker')['Close'].transform(lambda x: x.rolling(30).mean())

# Volatility — rolling 30-day standard deviation of daily returns
df['Volatility'] = df.groupby('Ticker')['Daily_Return'].transform(lambda x: x.rolling(30).std())
```

---

## 📊 Power BI Dashboard

The dashboard consists of **3 interactive pages** with full cross-filtering:

### Page 1 — Executive Home
- 4 KPI cards: Average Close, Total Volume, Average Return, Volatility
- Line chart: Stock Price Trend (2010–2026) with per-ticker toggle
- Table: Average Close, Daily Return, Volatility per ticker
- Bar chart: Total Trading Volume by Ticker

### Page 2 — Performance Analysis
- Horizontal bar: Total Growth % (2010–2026)
- Bar chart: Average Daily Return by Ticker
- Line chart: Close Price vs MA30 Moving Average
- Area chart: Daily Return Trend over time

### Page 3 — Risk Analysis
- Bar chart: Average Volatility ranking by Ticker
- Bubble scatter: Risk vs Return (bubble size = trading volume)
- Grouped bar: Return Distribution (Min / Avg / Max)
- Table: Full risk classification with color-coded Risk Level (Low / Medium / High)

---

## 🚀 How to Run

### Python Notebook

```bash
# Clone the repository
git clone https://github.com/yourusername/sp500-stock-analysis.git
cd sp500-stock-analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn plotly jupyter

# Launch notebook
jupyter notebook notebooks/S_P_500_Top_Stocks.ipynb
```

> Or open directly in **Google Colab** — the notebook is Colab-compatible.

### Power BI Dashboard

1. Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
2. Open `dashboard/S_P_500_Stock_Analysis_Dashboard.pbix`
3. Use the **Home / Performance / Risk** navigation tabs to explore pages
4. Use the **Ticker slicer** to filter by individual stocks

---

## 📋 Results Summary

| Ticker | Avg Close | Avg Daily Return | Volatility | Risk Level |
|--------|-----------|-----------------|------------|------------|
| META | $223.52 | 0.02% | 1.81 | Medium |
| MSFT | $151.83 | 0.04% | 1.25 | **Low** |
| TSLA | $101.70 | 0.03% | **2.96** | **High** |
| AMZN | $81.65 | 0.02% | 1.62 | Medium |
| AAPL | $78.80 | **0.05%** | 1.40 | Low |
| GOOG | $72.26 | 0.03% | 1.33 | Low |
| GOOGL | $72.17 | 0.02% | 1.32 | Low |
| AVGO | $47.17 | 0.03% | 1.88 | Medium |
| NVDA | — | **0.05%** | 2.33 | Medium |

> **Overall Portfolio:** Avg Close $92.60 · Avg Daily Return 0.03% · Avg Volatility 1.84 (Medium Risk)

---

## 📄 License

This project is for educational and portfolio purposes. Data sourced from Yahoo Finance.

---

## 🤝 Connect

If you found this project useful, feel free to ⭐ star the repo and connect!

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/chennakeshav-kanepogu-3b9084267/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?style=flat&logo=github)](https://github.com/keshavkhanepal)
