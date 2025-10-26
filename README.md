## 🧭 ETF vs Equally-Weighted Method

### 📘 Overview
This method compares the long-term performance of NASDAQ ETFs (which are value-weighted) with equally-weighted portfolios built from individual stocks.  
It provides a clear measure of whether large-cap companies (“leaders”) dominate sector performance or if smaller firms (“followers”) contribute significantly.  
The comparison can be applied both at the **global market level** and the **sector level** using available ETF and stock data.

---

### 📊 Method Summary

| Feature | ETF (Value-weighted) | Equally-weighted Portfolio |
|:--|:--|:--|
| **Weighting method** | Based on market capitalization | Same weight for each stock |
| **Representation** | Reflects performance of large-cap leaders | Reflects average performance of all firms |
| **Bias** | Dominated by large firms | Sensitive to small and mid-cap volatility |
| **Interpretation in project** | Captures sector leaders’ behavior | Captures followers’ collective behavior |
| **Data used** | ETF prices from *Dataset 1* | Individual stock prices (Dataset 1 + sector info from Dataset 2) |

---

### 🔁 Analytical Workflow

```mermaid
flowchart TD
    A[Dataset 1: Daily Prices (Stocks + ETFs)] --> B[Dataset 2: Sector & MarketCap Info]
    B --> C[Data Cleaning & Sector Matching]
    C --> D1[Compute ETF Returns]
    C --> D2[Build Equally-Weighted Portfolios per Sector]
    D1 --> E[Performance Metrics (Annualized Returns, Volatility)]
    D2 --> E
    E --> F[Compare ETF vs Equally-Weighted]
    F --> G[Interpretation: Leadership vs Follower Strength]
