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



# Polling and Callback

There are two common designs of execution logic. One is polling as the followings:

```python
# Polling
not_finish = True
while not_finish:
  # Get trading information
  signals = get_signals()
  # Fetch current position/balance
  current_position = get_positions(params)
  # Check criteria to trade
  if able_to_trade(signals, current_position):
    submit_order(signals)
  else:
    not_finish = False
```

The above is a pseudo code of a polling logic.  It heavily relies on rest API to fetch information like current position, price, volume, or other signals at each polling loop to determine whether it should break out from the loop. 

Advantages:

1. Easy to implement. The logic is synchronous and straightforward. The reason we don't use order information to determine whether current trade is finished is order submission and canceling frequency is much higher than position/balance change.

Disadvantages:

1. Resource Intensive: Polling can be extremely demanding on resources, particularly due to the rate limit of exchange APIs. It consumes significant request weight in each loop, which may be manageable for a single account but can quickly become problematic with multiple accounts and each is trading several instruments simultaneously.
2. Higher Latency:
   - API Blocking: The logic operates synchronously, which means the program waits while fetching (computing) the signals and cannot concurrently retrieve positions. This can introduce several blocking points within a single polling loop, further increasing response times.
   - Network Latency: Polling frequently demands substantial network resources as the system actively fetches updates from the server. This can lead to a backlog of packets, waiting for socket reads, which increases overall latency.
3. Redundancy of Resource Usage: Polling often leads to unnecessary data retrieval, fetching information such as prices and positions regardless of whether there have been any changes. This not only wastes resources but also adds to the inefficiency of the system.

The above latency or overheads caused might seem small, but will be accumulated at each polling loop. It eventually causes your order stay behind of the queue and takes longer time to be filled, which causes even more polling trials. It's a self reinforcement.





















