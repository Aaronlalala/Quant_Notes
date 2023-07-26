Exchange: OKX

When contracts of futures and options expire, settlement and delivery will occur.

The platform will calculate settlement prices using the time-weighted average of the [index prices](https://www.okx.com/markets/index/btc-usd) in the last hour before expiration and automatically transfer the profits or losses to users' accounts.

https://www.okx.com/help-center/7054474215309

(The index price is the BTC/USD price weighted from other 5 major exchanges.)

几个退仓的逻辑:

1. "The platform will calculate settlement prices using the time-weighted average of the index price in the last hour before expiration and automatically transfer the profits or losses to users' accounts."

   https://www.okx.com/markets/index/btc-usd

   最终交割合约用的交割价格是index price。是其他5个交易所的比特币/美元平均价。

2. 最近一笔6/30日交割日的最后一小时，仍然存在300-400的价差并不converge。

   ![image-20230724232315941](../../../../../Library/Application Support/typora-user-images/image-20230724232315941.png)

   ![image-20230724232414038](../../../../../Library/Application Support/typora-user-images/image-20230724232414038.png)

3. https://www.okx.com/help-center/7054474215309 根据okx的文档，币本位的delivery合约交割使用币结算交割。和之前Richard说的future实际不交割的说法有出入。

4. Notice that the leverage is considered in both long position and short position. For example, the initial capital is 1000 USD. Long side borrow 2000 USD and create 3000 USD short positions. Total leverage is 5.
