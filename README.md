## ETF vs Equally-Weighted Method

### 1. Overview
This method compares the long-term performance of NASDAQ ETFs, which are value-weighted, with equally-weighted portfolios built from individual stocks.  
It helps assess whether the overall market performance is mainly driven by large-cap firms (“leaders”) or whether smaller companies (“followers”) also play a significant role.  
The method can be applied both globally (entire market) and by sector, using the ETF and stock data available in our datasets.

---

### 2. Method Explanation

ETFs are value-weighted financial instruments, meaning that the weight of each stock in the portfolio is proportional to its market capitalization.  
In practice, this implies that a company such as Apple or Microsoft contributes much more to the ETF’s overall return than a small-cap stock.  
Thus, ETFs largely reflect the behavior of the market leaders within each sector.

By contrast, an equally-weighted portfolio assigns the same weight to each stock, regardless of its market capitalization.  
This portfolio can be seen as the average performance of all firms, where large and small companies have the same influence.  
In an equally-weighted setup, each stock represents a fraction 1/n of the portfolio, where n is the total number of firms included.  
Such a portfolio is rebalanced regularly (e.g., daily, weekly, or monthly) to maintain equal weights as prices evolve.

The difference between value-weighted and equally-weighted performances provides a clear measure of how much large companies dominate market movements.  
If the ETF (value-weighted) outperforms the equally-weighted portfolio, it suggests that sector performance is mainly driven by the largest firms.  
If the equally-weighted portfolio performs better, smaller firms have had a greater contribution or higher growth relative to the leaders.

For sector-level analysis, we can construct an equally-weighted portfolio using all firms belonging to a given sector (as defined in Dataset 2) and compare it with the corresponding sector ETF included in Dataset 1.  
This allows us to assess leadership effects within each specific industry, such as technology, healthcare, or energy.

---

### 3. Analytical Workflow

The analysis relies on two complementary datasets:

- **Dataset 1 – Stock Market Dataset (NASDAQ historical daily prices)**  
  Contains daily prices (Open, High, Low, Close, Adjusted Close, and Volume) for both ETFs and individual stocks.  
  These data are used to compute daily returns, cumulative returns, and volatility for each instrument.

- **Dataset 2 – NASDAQ Company List**  
  Provides metadata including Symbol, Name, MarketCap, Sector, and Industry.  
  This dataset allows us to group companies by sector and classify them according to their market capitalization.

Using these datasets, the steps are as follows:
1. Match each stock from Dataset 1 with its corresponding sector and market capitalization from Dataset 2.  
2. For each sector, compute the equally-weighted portfolio return by averaging the daily returns of all firms in that sector.  
3. Retrieve the relevant ETF prices (global or sector-specific) and compute their daily and annualized returns.  
4. Compare the cumulative and annualized performances of the ETF and the equally-weighted portfolio to measure the dominance of large firms over smaller ones.  
5. Extend the analysis to compare results across sectors and during different market conditions (calm vs volatile periods).

---

### 4. Note on Data Bias

This analysis may be affected by **survivorship bias**, since the dataset includes only companies that were still listed on NASDAQ in 2020.  
This can overstate the average performance of small firms that survived while excluding those that exited earlier.  
To mitigate this effect, results will be compared with ETF performance, which reflects continuous index rebalancing and company turnover.

---
