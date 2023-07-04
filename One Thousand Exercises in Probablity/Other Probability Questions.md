# Derangement Problem

**Question:** 12 partygoers throw their hats into a pile. After the party, when they leave in a hurry, each picks a hat from the pile at random. What's the expected number of partygoers who leave with their own hat? What is the standard deviation?

**Solution:** assume there are n people. Each person has probability $\dfrac{1}{n}$ picking its own hat. (It's counter intuitive but could be proved with conditional probability). Let $X_i$  denotes whether i-th person gets the correct hat and $Y = \Sigma_iX_i$. $E(Y) = E(\Sigma_iX_i) = \Sigma_iE(X_i) = n \cdot \dfrac{1}{n} = 1$.

$Var(Y) = E(Y^2) - E^2(Y)$. $E(Y^2) = E(\Sigma_iX_i \cdot\Sigma_iX_i) = \sum_i\sum_jE(X_iX_j)$. 

$E(X^2) = \dfrac{1}{n}$ and $E(X_iX_j) = \dfrac{1}{n(n - 1)}$ $\rightarrow$ $Var(Y) = 1$.

