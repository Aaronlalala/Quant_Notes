# Trade Terminal

## What is Cluster Placement Groups

Instances in a cluster placement group are placed physically close to each other, which optimizes the network latency and throughput. Thus, the TCP communications among these instances could have lower latency and have higher throughput. It requires all instances are in the same availability zone. After you start an instance, you could have a cluster placement group id of it. You could have limit number of instances to place together. Just follow the UI instruction to launch the instances.

## AZ Collocation

Simple but the most effective way to reduce the latency. If you know which az the exchange put their servers at, you start your instances in the same one. 

Another similar strategy is to use the same instance type as the exchange. Those, instances were built in batch. The same types are put together. Using the same type of instance of the exchange, let you have a closer distance within an AZ.

## Hunt Instance Strategy

Random start large number of instances within the same AZ. Start the measuring script to record latency. Keep the good ones and terminate the bad ones.

After some time, you will have some instances that have lower latency. Then you could collocate with thouse instances using cluster placement groups.

## Busy Read and Poll

Busy poll mode reduces latency on the network receive path. When you enable busy poll mode, the socket layer code can directly poll the receive queue of a network device.

Busy poll could set the time wait for event arrival check (websocket message). Busy read defines the latency wait for network packets read. 

Not very useful in crypto makets, because the ws frequency is usually much higher than the default value 50 (100 ms to 500 ms).s

## Interruption Handling

For multi-core instances, we disabled irqrebalance by default which forces CPUs to handle interrupts evenly, bound all network card interrupts to a specific core and made other cores dedicated to run the actual application. This approach helps in reducing competition for CPU resources, as the cores dedicated to the script won't be frequently interrupted for IRQ processing.

Follow the RedHat's real-time system tuning manual.

## Remote Procedure Call

It allows a local instance to execute a procedure on a remote instance. I think it's similar to a self-defined API. We use this technique to upgrade our trading system. Originally, our trading logic is polling. Thus, it consumes lots of resources waste (rate limit of api). For exmaple, we poll the price, positions, or orders. However, those things' status do not change. Thus, we want to change this logic to call back. However, this will completely change the system which cause lots of work and pain. Thus, we implemented a server which use WebSocket to subscribe those information from the exchange, only updating when there is a change. Then, we only poll from our own servers instead of polling the exchange, avoiding the api rate limit. In this way, we could also separate the strategy, execution and market/account information.

## Why Use Redis

It's easy to use and it dictionary data structure fit the context. Because we have different ticker's symbol unique. Each instrument has its own property and data.

## Virtual Private Cloud

We use this for security. We're using RPC to for instances communication and we don't want our network packets being captured by others. We have lots of instances. Instead of configue instances one by one, we create a VPC to provide a isolated network.

Potential VPC peering in the future with exchanges.

## Order Book Simulators

We have order book delta in binarys and we know the offsets meaning. For example, the first 8 bytes is for the number of bid layers, the 9-16 bytes are for the number of ask layers. What I did is to transform those binarys into actual human readable data and keep applying them to the snapshot of the orderbook at every timestamp. Then, i got an orderbook replay. We could then use this for backtesting or research.

