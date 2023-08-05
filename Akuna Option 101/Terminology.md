# Terminology

## General

- Bid: the highest price someone is willing to buy.

- Offer: the lowest price someone is willing to sell.

- Size: the amount of contracts one is willing to trade at a price.
- Make a market: to provide a bid and ask price and sizes for each.
- Spread: the difference between the bid and ask prices.
- Hedge: a trade to reduce the price changes.
- Paper: the interested parties trade against us. (or other market makers.)
- Broker: intermediate people.
- Tick size: the smallest change per change.
- Queue priority: who is first in line to be executed. Usually, ordered by price first then time.

## Order Types

- Immediate or cancel orders (IOC): a type of order requires all part of order to be executed immediately. The unfilled part will be canceled immediately.

- Good for day orders (GFD): a type of order that remain active untill all parts filled or end of the trading day.

- Good till canceled (GTC): a type of order that will remain active until completed or canceled.

- All or None: either executed completely or not executed at all.

- Fill or kill: must be executed in its entirety immediately or be canceled.

- One cancels the other: when one order is executed, the other is canceled automatically.

  ![OCO](../Figures/OCO order.png)