# Risk Model

**What is Risk?**

The unintentinal exposures that are linked to the persuit of alpha. And those exposures are not expected to make money. 

For example, if you think stock A outperforms stock B. Only opening long position for stock to persuit this alpha, will be exposed to market direction risks.

Risk models are like pessimists. Risk models exist largely to control the size of desirable exposures or to deal with undesirable types of exposures.

**Two Ways to Measure Risks:**

1. Volatility

   Volatility is a general idea that measures changes of the target. Specifically, it could different formulas. 

   - The most common one is the **simple variance** $\sigma^2$ over the past time window. For the simple variance, the second order terms of price change is equally weighted.
   - Based on that, there is another exponentially weighted moving average (**EWMA**) method that recursively allocate more weights on recent changes to compute this "variance". That is, $\sigma^2_n = \lambda\sigma^2_{n-1} + (1 - \lambda) \delta^2$.
   - GARCH: similarly, but $\sigma_n^2$ is a more general function of $\sigma_{n-1}^2$ and $\delta^2$.

2. Dispersion
   1. Cross sectional standard deviation
   2. Correlation and covariance

**Value at Risk Model**

It estimates how much a portfolio can gain or lose within a given confidence interval. It has three parameters, time window, confidence interval and PNL limit. For example:

If a portfolio of stocks has a one-day 95% VaR of 1 million, that means that there is a 0.05 probability that the portfolio will fall in value by more than 1 million over a one-day period if there is no trading.



## Theory Driven Risk Models

“Theory-driven risk modeling typically focuses on named or systematic risk factors”. Those models are based on some defined economic concepts. Investors who apply those models keep the faith that those underlying theory are true.

1. Diversification risk.
2. Market cap.
3. Interest rate risk.

## Empirical Risk Models

More adaptive and based on historical data. They are not try to explain the market. They make decisions based on data.

For example, GARCH model. It uses historical data to measure the volatility of the assets.