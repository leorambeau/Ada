### Survivorship Bias

A general limitation that affects all analyses in this project is the presence of survivorship bias.  
Because the NASDAQ dataset only includes companies that were still active and listed in 2020, firms that went bankrupt, were delisted, or merged before that date are missing from the data.  
This exclusion primarily affects small and mid-cap firms, which are more likely to disappear over time, and may lead to an overestimation of their average performance or an underestimation of market volatility.  
To reduce the impact of this bias, the project compares results with global and sectoral ETFs, which are continuously rebalanced and therefore reflect firm turnover.  
Additional robustness checks—such as dividing firms into size categories, using shorter time windows, and cross-validating with sector-level aggregates—help ensure that observed leader–follower patterns are not driven by sample survivorship.
