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

















