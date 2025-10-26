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
| **Economic meaning** | Reflects the performance of sector leaders | Reflects the average performance of all firms |
| **Interpretation in this project** | Measures performance driven by market leaders | Captures the collective behavior of followers |

By comparing their respective performances, we can evaluate the dominance of large firms.  
If the ETF outperforms the equally-weighted portfolio, sector performance is likely driven by large-cap leaders.  
Conversely, if the equally-weighted portfolio performs better, small and mid-sized firms are playing a greater role in driving returns.  
At the sector level, the same comparison can be made using the relevant sector ETF (from Dataset 1) and the equally-weighted portfolio of all firms belonging to that sector (from Dataset 2).

---

### 3. Analytical Workflow

The analysis relies on two complementary datasets:

- **Dataset 1 – Stock Market Dataset (NASDAQ historical daily prices)**  
  Contains daily prices (Open, High, Low, Close, Adjusted Close, and Volume) for both ETFs and individual stocks.  
  These data are used to compute daily returns, cumulative returns, and volatility for each instrument.

- **Dataset 2 – NASDAQ Company List**  
  Provides metadata including Symbol, Name, MarketCap, Sector, and Industry.  
  This dataset allows grouping companies by sector and ranking them by market capitalization.

**Implementation steps:**
1. Match each stock from Dataset 1 with its corresponding sector and market capitalization from Dataset 2.  
2. For each sector, compute the equally-weighted portfolio return by averaging the daily returns of all firms in that sector.  
3. Compute ETF returns using the sector or global ETFs available in Dataset 1.  
4. Compare cumulative and annualized performances between the ETF and the equally-weighted portfolio to evaluate leadership effects.  
5. Extend the analysis by observing variations across sectors and between stable and volatile market periods.

---

### 4. Note on Data Bias

This analysis may be affected by **survivorship bias**, since the dataset includes only companies that were still listed on NASDAQ in 2020.  
This can overstate the average performance of small firms that survived while excluding those that exited earlier.  
To mitigate this effect, results are compared with ETF performance, which inherently reflects continuous rebalancing and company turnover within the index.

---
