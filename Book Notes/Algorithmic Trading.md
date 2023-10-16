# Mean Reversion Basics

## Mean Reversion Types

Time series mean reversion and cross-sectional mean reversion.

## Cointegrating

Prices, in the most cases, are not stationary. But we could combine two or more instruments that are not mean reverting into a portfolio whose market value is mean reverting. Those instruments are called cointegrating.



## Stationary and Mean Reverting

The mathematical description of a mean-reverting price series is that the change of the price series in the next period is proportional to the difference between the mean price and the current price.  -> ADF test to test whether proportional constant is zero

The mathematical description of a stationary price series is that the variance of the log of the prices increases slower than that of a geometric random walk. (diffuse slower than geometric random walk)

## Linear Model of Price Changes

$\Delta y(t)=\lambda y(t-1)+\mu+\beta t+\alpha_1 \Delta y(t-1)+\cdots+\alpha_k \Delta y(t-k)+\epsilon_t$, where $\Delta y(t) \equiv y(t)-y(t-1), \Delta y(t-1) \equiv y(t-1)-y(t-2)$

## Augmented Dickey-Fuller Test

Test a seires is stationary or not.

## Hurst Exponent

H < 0.5 indicates a mean-reverting series. H = 0.5 indicates a random walk. H > 0.5 incidates a trending series.

## Half Life of Mean Reversion

$\lambda$ seeing from the perspective of stochastic calculus, it's the half life of the mean revertin process. Sometimes, we fail to reject the hypothethis that the series is random walk. But it does not mean we cannot trade it by computing the half life.

Fit a linear regression on delta y and y_lag 1. Then the half life is computed as $-\dfrac{log(2)}{\lambda}$. If the half life is suitable for our trading horizon, we could still trade this instrument.

Simple Signal: assume $\delta$ is the half life:  $\dfrac{y - MA(\delta)}{MSTD(\delta)}$. 

## Cointegrated Augmented Dickey-Fuller Test

It's similar to ADF test. However, it's applied to residuals from a cointegrated relation. Cointegrated relation could be formed by simple linear regression. This could be tried with different instuments as response and independent variable. Then select the hedge ratio using p-value of the test.



## Johansen Test

Test cointegration for more than two instruments. Python [statsmodel](https://www.statsmodels.org/dev/generated/statsmodels.tsa.vector_ar.vecm.coint_johansen.html). Eigenvector is the hedge ratio. Large eigenvector indicates stronger cointegrated relation.

Then, we use the eigenvector to form a stationary series and find the half life.

## Summary

ADF Test -> CADF Test -> Johansen Test: from univariate to bivariate to multivariate test.

After we got the stationary seires, we compute the half-life. Then, generate signals.

Generally, there is a fundamental story behind two cointegrated pairs or set.