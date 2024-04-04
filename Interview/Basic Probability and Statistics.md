[toc]

## Bayes' Theorem

$P(A|B) = \dfrac{P(B|A) \cdot P(A)}{P(B)}$. This formula could be derived by the **conditional probability formulas**:

$P(A|B) = \dfrac{P(A \cap B)}{P(B)}$ and $P(B|A) = \dfrac{P(A \cap B)}{P(A)}$. 

In most cases, when the probability $P(A|B)$ and $P(B)$ cannot be computed directly, $P(B|A)$ and $P(A)$ are easier to compute. Then we use **total probability theorem** to compute the denominator,

$P(B) = \sum_{i} P(B|A_i) \cdot P(A_i)$. (The same as computing the marginal distribution of B)

The above formulas do not depend on independency.

In addition, the probability of the **union of events** is $P(A\cup B) = P(A) + P(B) - P(A\cap B)$. And to compute the intersection of events, we might need to use conditional probability.

## Law of Large Number

If you sample a random variable independently a large number of times, the sample mean will converge to that random variable's true expectation.

## Central Limit Theorem

Same setting as LLN, the distribution of sample mean will approach a normal distribution. 

$\bar{X} = \dfrac{X_1 + X_2 + ... + X_n}{n}$ will approch $N(\mu,\, \dfrac{\sigma^2}{n})$, and it could be converted to standard normal distribuiton.

## Joint Distribution

Marginal Distribution: only focus a subset of variables from a joint distribution. 

For 2-dimensional discrete case:

$P(X = x) = \sum_{y \in Y} P(X = x, Y = y)$

$P(Y = y) = \sum_{x \in X} P(X = x, Y = y)$

For continuous case, it's also the same

$f_X(x) = \int_{y \in Y} f_{XY}(x, y) \, dy$

$f_Y(y) = \int_{x \in X} f_{XY}(x, y) \, dx$

## Hypothesis Testing

**P-Value:** Given the null hypothesis is true, p-value is the probability to get a more extreme (at least as extreme) sample than the test statistic. 

### Test Statistics

It's a function of your sample data and gives a summary. If we know the distribution of test statistic, we could just use it to compute the p-value. Otherwise, we use central limit theorem to standardize it to normal distribution or t distribution.

**Z-Test and t-Test**

These two statistics are used test the mean. If we know the theoretical variance of the distribution, transform the test statistics to the standard normal $\dfrac{\bar{x} - \mu_0}{\sigma/\sqrt{n}}$. However, if we don't know the theoretical variance of the distribution, we transform the test statistics to student t distribution $\dfrac{\bar{x} - \mu_0}{s/\sqrt{n}}$, where $s^2 = \dfrac{\sum (x_i - \bar{x})^2}{n-1}$

**Chi-Squared Test**

It's used to test the goodness of fit, $\chi^2 = \sum_i \dfrac{(O_i - E_i)^2}{E_i}$, $O_i$ is the observed output, and $E_i$ is the expected value. As mentioned earlier, this test statistic also measures how the sample data is deviated from the expected value under the null hypothesis. And It is contructed like that to follow a chi-squared distribution so that we could compute the p-value.

### Confidence Interval

We could derive the C.I. using p-value.

### Type 1 and Type 2 Error

Type 1 error is rejecting the null hypothesis when it's correct. Type 2 error is failing to reject the null hypothesis when it's false.

How to compute the probability of getting type 1 or type 2 error?



## Method of Moment

It's a method to estimate the parameters of a distribution. The idea is to use sample moments to estimate the theoretical moments. Moments are measures of the shape of the distribution. The first moment is the mean, and the second moment is the variance.

To estimate, we compute the sample moment and write down the expressions of theoretical moments. Then, we solve the equation.