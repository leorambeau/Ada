## ETF vs Equally-Weighted Method

### 1. Overview
This method compares the long-term performance of NASDAQ ETFs, which are value-weighted, with equally-weighted portfolios built from individual stocks.  
It helps assess whether overall market performance is mainly driven by large-cap firms (“leaders”) or whether smaller companies (“followers”) also play a significant role.  
The method can be applied both globally (entire market) and by sector, using the sectorial ETFs and stock data available in our datasets.

---

### 2. Method Explanation

ETFs and equally-weighted portfolios differ mainly in how they assign weights to each company within the portfolio.  
While ETFs are **value-weighted**, giving more importance to large firms with higher market capitalization, equally-weighted portfolios treat every company the same, regardless of size.  
This structural difference allows us to measure whether the performance of a sector or the overall market is concentrated among large firms or shared more evenly across all companies.

| Feature | ETF (Value-weighted) | Equally-weighted Portfolio |
|:--|:--|:--|
| **Weighting principle** | Each stock’s weight is proportional to its market capitalization | Each stock has the same weight (1/n) |
| **Main contributors** | Large-cap companies dominate returns | All firms contribute equally |
| **Interpretation in this project** | Measures performance driven by market leaders | Captures the collective behavior of followers |

By comparing their respective performances, we can evaluate the dominance of large firms.  
If the ETF outperforms the equally-weighted portfolio, sector performance is likely driven by large-cap leaders.  
Conversely, if the equally-weighted portfolio performs better, small and mid-sized firms are playing a greater role in driving returns.  
At the sector level, the same comparison can be made using the relevant sector ETF (from Dataset 1) and the equally-weighted portfolio of all firms belonging to that sector (from Dataset 2).

---

### 3. Implementation with the Data

The analysis relies on our two datasets:

- **Dataset 1 – Stock Market Dataset (NASDAQ historical daily prices)**  
  Contains daily prices (Open, High, Low, Close, Adjusted Close, and Volume) for both ETFs and individual stocks.  
  These data are used to compute returns and risk metrics.

- **Dataset 2 – NASDAQ Company List**  
  Provides metadata including Symbol, Name, MarketCap, Sector, and Industry.  
  This dataset allows grouping companies by sector and identifying firm size (leaders vs followers).

**Implementation steps:**

1. **Data preparation:**  
   Match each stock from Dataset 1 with its corresponding sector and market capitalization from Dataset 2.

2. **Global analysis:**  
   - Build an **Equally-Weighted (EW) global portfolio** including all stocks in the dataset.  
   - Compute the performance of **global ETFs** available in Dataset 1.  
   - Compare both using key performance metrics:  
     - **Cumulative returns** (overall growth over time),  
     - **Annualized returns** (average yearly growth),  
     - **Volatility** (standard deviation of daily returns),  
     - **Sharpe ratio** (risk-adjusted performance).  

3. **Sector-level analysis:**  
   - For each sector identified in Dataset 2, construct an **Equally-Weighted sector portfolio** averaging the returns of all companies in that sector.  
   - Retrieve and analyze the **corresponding sector ETFs** from Dataset 1.  
   - Compare performance across sectors using the same metrics as above to assess whether leadership dominance varies by industry.

4. **Interpretation:**  
   Evaluate whether large-cap firms (represented by ETFs) dominate performance globally and within sectors, and whether small and mid-cap companies exhibit stronger relative returns during specific market conditions (e.g., high volatility periods).

---
