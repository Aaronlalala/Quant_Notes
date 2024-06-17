- [Constant product formula](https://docs.uniswap.org/contracts/v2/concepts/protocol-overview/how-uniswap-works)
- Does price fluctuation always cause liquidity provider lose money? I think yes.
- [Uniswap pool arbitrage](https://www.youtube.com/watch?v=9EKksG-fF1k) optimal amount calculation.
- [Uniswap white paper v2](https://uniswap.org/whitepaper.pdf)

# Arbitrage Logic

There are two pools, A and B. For simplicity, we use X and Y to replace the symbol of actual coin. If we observe a deviation of the relative price from two pools, we arb the spread. The followings are computation of optimal amount to trade and profits.

## Variable Definitions

$f$: is the trading fee.

$X_A$: reserve of X in pool A.

$Y_A$: reserve of Y in pool A.

The same for $X_B$ and $Y_B$.

$dy_A$: the number of coins A we input in the pool A.

$dy_B$: the number of coins A we receive from the pool B.

$F(dy_A) = dy_B - dy_A$ is the profit generated from an arbitrage trade. 

$dx$: amount of coins we receives from the pool A.

## Optimal Trade Given Status of Two Pools

Without loss of generality, we assume that the relative price of coin Y in pool A is lower than the pool B. To further simplify the problem, we assume only input charges a fee and output does not charge, otherwise, there are just too many terms to compute.

$dx = \dfrac{dy_A(1 -f)X_A}{Y_A + dy_A(1 - f)}$

$dy_B = \dfrac{dx(1-f)Y_B}{X_B + dx(1-f)}= \dfrac{\dfrac{dy_A(1 -f)X_A}{Y_A + dy_A(1 - f)}(1-f)Y_B}{X_B + \dfrac{dy_A(1 -f)X_A}{Y_A + dy_A(1 - f)}(1-f)}$, which can be simplified as

$\dfrac{dy_A(1-f)^2X_AY_B}{Y_AX_B + dy_A(1-f)X_B + dy_A(1-f)^2X_A}$

**Profit function** is $F(dy_A) = \dfrac{dy_A(1-f)^2X_AY_B}{Y_AX_B + dy_A(1-f)X_B + dy_A(1-f)^2X_A} - dy_A$. The we solve the optimal value of coin A amount to swap, and plug in all information to the profit function, if it's positive, it triggers the arbitraging trade.

Since we're assuming the price of coin Y in pool A is lower than the price of coin Y in pool B, the $F'(dy_A)= 0$ yields the local maximum.

Let $dy_B = \dfrac{dy_A(1-f)^2X_AY_B}{Y_AX_B + dy_A(1-f)X_B + dy_A(1-f)^2X_A} = \dfrac{f}{g}$. $F' = 0$ is equivalent to $f'g-fg' = g^2$.

$f'g-fg' = (1-f)^2X_AY_BY_AX_B$

$g^2 = k^2(dy_A)^2 + 2kY_AX_Bdy_A + (Y_AX_B)^2$, by assinging $k = (1-f)X_B + (1-f)^2X_A$.

So we have the optimal equation $k^2(dy_A)^2 + 2kY_AX_Bdy_A + (Y_AX_B)^2 - (1-f)^2X_AY_BY_AX_B = 0$, which is in quadratic form $ady_A^2 + bdy_A + c = 0$.

Thus, we use the optimal formula $\dfrac{-b + \sqrt{b^2-4ac}}{2a}$ to solve and we eliminate the negative result.