# Derangement Problem

**Question:** 12 partygoers throw their hats into a pile. After the party, when they leave in a hurry, each picks a hat from the pile at random. What's the expected number of partygoers who leave with their own hat? What is the standard deviation?

**Solution:** assume there are n people. Each person has probability $\dfrac{1}{n}$ picking its own hat. (It's counter intuitive but could be proved with conditional probability). Let $X_i$  denotes whether i-th person gets the correct hat and $Y = \Sigma_iX_i$. $E(Y) = E(\Sigma_iX_i) = \Sigma_iE(X_i) = n \cdot \dfrac{1}{n} = 1$.

$Var(Y) = E(Y^2) - E^2(Y)$. $E(Y^2) = E(\Sigma_iX_i \cdot\Sigma_iX_i) = \sum_i\sum_jE(X_iX_j)$. 

$E(X^2) = \dfrac{1}{n}$ and $E(X_iX_j) = \dfrac{1}{n(n - 1)}$ $\rightarrow$ $Var(Y) = 1$.



# Geometric Distribution Problem

**Question:** A breakfast cereal company gives away a free toy in each box of cereal. There are four diﬀerent toys. How many boxes do you expect to have to buy in order to get all four toys? 

**Solution:** 

**Method 1:** directly write out the recursive function. Assume we need to collect $T$ different toys. After we collected $(t-1)$ toys, the probability that we get the t-th toy in one draw is $p_t = \dfrac{T - (t - 1)}{T}$. Let $N_t$ be the number of draws required to obtain the t-th unique toy. $E(N_t) = p_t \cdot 1 + (1 - p_t) \cdot(1 + E(N_t)) \to E(N_t) = \dfrac{1}{p_t} = \dfrac{T}{T - t + 1}$. Let $N$ be the total number of draws to collect all toys. $E(N) = E(N_1 + N_2 + ... + N_T) = \sum_{t=1}^{T} N_t = T \sum_{t=1}^T\frac{1}{t}$. Thus, for plug in $T = 4$ to get the result.

**Method 2:** actually every time we try to get a new different toy, it's a Bernoulli trial. The number of trials until the success follows geometric distribution. Thus, we get $E(N_t) = \frac{1}{p_t}$ directly. With this knowledge, we could also compute the variance of this process. $Var(N) = \sum Var(N_t)$ and $Var(N_t) = \dfrac{1 - p_t}{p_t^2}$.
