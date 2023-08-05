# Introduction

**Exchange:** OKX

**Instruments:** BTC spot, BTC quarterly deliver contract (used-margin + crypto-margin). 

**Frequency:** Low frequency.

**Position Capacity:** 5 - 10 million.

**Commission:** let limit commission and market commission be $x$ and $y$ respectively. We use limit order to open positions at both sides. When is about to settle, we use limit order to close spot. The settlement requires market commission. Total commission is $3x + y$. 

# Strategy

## General Idea

It's a classic cash and carry strategy. There is a significant spread between spot and quarterly deliver future price on OKX. Thus, long crypto spot and short equal amount of contract. Hold positions and assets until settlement date. Then close the position of spot.

## Procedures

1. **Entry Signal**: let price of spot and futures be $p_{s}$, $p_f$ respectively. Let days till settlement be $t_{\Delta}$. $\dfrac{\frac{p_f}{p_s} - 1}{t_{\Delta}} \cdot 365 \geq \gamma_1$ is the entry signal.
2. **Exit Signal**: $\frac{p_f}{p_s} - 1 \leq \gamma_2$.
3. **Split orders**: we split the expected position into mini-batches with value $\delta_1$. Everytime, we receive a signal, we enter or exit a mini-batch position.
4. **Roll Over:** Let $p_{nf}$ denote the price of next quarter future. When we receive exit signal, we could choose to roll over to the next quarter contract if $\dfrac{\frac{p_{nf}}{p_x} - 1}{\Delta t} \geq \gamma_1$.
5. **Close long positions**: since the settlement price is the time-weighted index price an hour before settlement. We evenly close our long positions with mini-batches $\delta_2$ starting from an hour earlier.

# Backtest

## Thresholds need to define

1. Entry signal's $\gamma_1$.
2. Exit signal's $\gamma_2$.
3. Enter and exit order batch value $\delta_1$.
4. Close batch value $\delta_2$

## Data

15min-tick OHLC data for BTC futures and spot.

## Procedures

1. In most conservative estimate, we compute the low of $p_f/p_s$. Use recent 6-month data's distribution to select a percentile. The specific value of $\gamma_1$ depends on expected time we want to completely allocate our capital.
2. Enter batch value $\delta_1$ is could be small. Since we might tolerate 2 weeks to open positions.
3. Fetch average open price of our short position. Compute PNL using current price and average open price to determine whether exit one batch now.
4. Close batch depends on the size of our long positions and the size of best ask of the order book. Each batch value should be smaller than the an predefined percent of the best ask size. It should also make sure we could close long positions in one hour.

# Execution

1. Layering orders: if I put all orders in the best ask and price goes up suddenly, I only enter the market at that lowest ask price. However, if I put multiple layers of orders, I could have a better average entry price if market suddently goes up.

2. Order book analysis: 

   1. Order book imbalance.
   2. Large size orders

   use the size of best bid and best ask to predict short term price movement. Suppose, if there is a large size of orders at the first ask of the future, the price will go down shortly with high probability. The idea case is that I check the spread is greater than the threashold. At the same time, spot's first ask size is large and future's bid size is also large, which indicates the spread will continue to enlarge.

3. Short term price prediction.

   1. Ask Allen.

## How to compare differnt methods

1. Condition 1: large spread then enter.
2. Operation 1: multiple layers of orders to get better average price.
3. Operation 1 variant: since spot is more liquid and contracts are less. Maybe we could place multiple layers that spot and only one layer at contracts. Then, now two side will have similar speed to open positions while spot side could get a better price.
4. Condition 2: advantageous imbalance structure of order book, then enter.
5. Operation 2: use stop-limit orders to prevent lost at one side if market moves drastically. 
