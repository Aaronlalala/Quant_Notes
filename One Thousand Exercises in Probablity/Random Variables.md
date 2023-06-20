# Question 2

Compute the distribution of a function of a random variable. Given cumulative distribution function of $X$ is $F(x)$, need to compute the cdf of a function $Y = aX+b$. 
$$
G(Y) = P(Y \leq y) = P(aX + b \leq y)\\
\text{if a $\geq$ 0: }P(aX + b\leq y) = P(X\leq \frac{y-b}{a}) = F(\frac{y-b}{a})\\
\text{else: }P(aX + b\leq y) = P(X\geq \frac{y-b}{a}) = 1- F(\frac{y-b}{a})
$$
Then we could further use derivative to compute the pdf of the distribution.
