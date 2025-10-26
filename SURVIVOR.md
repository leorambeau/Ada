### Survivorship Bias

A general limitation that affects all analyses in this project is the presence of survivorship bias.  
Because the NASDAQ dataset only includes companies that were still active and listed in 2020, firms that went bankrupt, were delisted, or merged before that date are missing from the data.  
This exclusion primarily affects small and mid-cap firms, which are more likely to disappear over time, and may lead to an overestimation of their average performance or an underestimation of market volatility.

#### How to limit this bias
One possible way to reduce survivorship bias is to shorten the analysis window to recent years, such as 2015–2020, when the probability of firm disappearance is lower.  
Another complementary approach is to **weight companies according to their lifespan on the market**, using the *IPOyear* information available in Dataset 2.  
Firms that have been listed for a longer period can be assigned a higher weight, as they represent a more stable segment of the market, while recently listed firms—more likely to drop out of the dataset—receive lower weights.  
Finally, comparing results with ETF data, which are continuously rebalanced and automatically adjust for company entry and exit, provides an additional robustness check against this bias.
