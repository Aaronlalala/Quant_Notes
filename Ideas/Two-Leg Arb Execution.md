[toc]

# Two-Leg Arb Strategy

## Natural Spread

Legs have a natural price spread, this is because one leg is spot and another leg is contract. The contract could have larger leverage, thus, it moves faster than spot, causing a spread, that will shortly converge by funding rate mechanism. We could utilize this to find a good timing to open or close positions.

## Execution Method

### BBO Makers

Constantly submit limit orders at BBO prices. 

Pros: easy to understand, lower commission.

Cons: 

- two legs has no promise to execute at the same price. For example, when your short leg is filled and market continusouly goes up, your long leg BBO limit cannot be filled. It will end up being filled at a much higher price.
- It might take long time, because market can go in one direction.

Some justifications:

1. Enter the leg with lower liquidity first. The other leg will be filled faster as it has larger volume.
2. Submit the order parallely. You will be placed at the fronter of the queue.

### BBO Maker + Taker

BBO maker leg first. Once it's filled, use market order to enter another leg.

Pros: it's fast and the worst result is promised.

Cons:

- Higher commission fee. Usually, market order commision is 10 bps.
- You lost at the first, market order will cross the BBO, so you at least will lose 1 tick size spread.

Justification

- Do not use market order directly. Instead, place cross BBO limit order to take. Because, sometimes you could take multiple layers, or the market goes worse suddenly and you have no control of this order's worst price. The goal is the same, however, cross BBO limit order is more controlable.

Generally, I think the above two methods have similar performance regarding entry price spread, considering that two makers have a commission advantage, though sometimes it could have very bad results. 

However, without doubt that BBO maker + taker is faster.
