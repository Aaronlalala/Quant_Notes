# Static Game Setting

1. All agents simultaneously choose strategies
2. Noncooperative game
3. Complete information: player's strategies are common knowledge
4. One-shot game or extensive form
5. Each player's feasible set of strategies must be independent of the strategies chosen by the other players, i.e., the strategy chosen by one player should not limit the choice of other players. 

## Best Response Functions and Equilibrium

Given n-player game, player i's best response function to the strategies $x_{-i}$ of the other players is the strategy that maximizes player i's payoff.

All players choose their best responses is a candidate for noncooperative solution, and such an outcome is called Nash Equilibrium.

Two problems of Nash Equilibiurm, one is existence and the other is uniqueness.

- Optimal solution (i.e., a solution that maximizes the sum of players' payoffs) need not be an NE.
- NE may not even be Pareto optimal.

## Existence of Equilibrium

There are three fixed-point theorems to prove.

**Theorem 1**

Suppose that for each player, the **strategy space is compact** and convex and the payoff function is continuous and **quasiconcave** with respect to each player’s own strategy. Then, there exists at least one pure strategy NE in the game.

**Theorem 2**

Suppose that a game is symmetric, and for each player, the strategy space is compact and convex and the payoff function is continuous and quasiconcave with respect to each player’s own strategy. Then, there exists at least one symmetric pure strategy NE in the game.

**Theorem 3**

In a supermodular game, there exists at least one NE.

A twice continusouly differentiable payoff unction $\pi_i(x_1, ..., x_n)$ is super modular iff $\pi''_i(x_i, x_j) \geq 0$ for all x and $j \neq i$. The game is called supermodular if the players payoffs are supermodular.

## Uniqueness of Equilibrium

Demonstrating uniqueness is generally much harder than demonstrating existence of equilibrium. The following methods prove the uniqueness of NE give that NE exists. It this condition is not given, it needs to be proved separately.

Finally, it is worth pointing out that uniqueness results are only available for games with continuous best response functions and, hence, there are no general methods to prove uniqueness of NE in supermodular games.

**Method 1. Algebraic Argument**

Simply looking at the optimality conditions to see if it's unique. For example, in a two-player game, the optimality condition of one player may have a unique closed-form solution that does not depend on the other player’s strategy, and, given the solution for one player, the optimality condition for the second player can be solved uniquely. In other cases, one can assure uniqueness by analyzing geometrical properties of the best response functions and arguing that they intersect only once (only feasible in two-player games).

**Method 2. Contraction Mapping Argument**

It's easiest to verify. A mapping is a contraction if it brings points closer.

**Theorem 4**

If the best response mapping is a contraction on the entire strategy space, there is a unique NE in the game.

One can think of a contraction mapping in terms of iterative play: Player 1 selects some strategy, then player 2 selects a strategy based on the decision by player 1, etc. If the best response mapping is a contraction, the NE obtained as a result of such iterative play is stable but the opposite is not necessarily true. The best response will bring the following strategies "closer". 

**Method 3. Univalent Mapping Argument**

If the best response mapping is one to one, then there can be at most one fiexed point of such mapping.

**Theorem 6**

Cannot understand.

**Method 4. Index Theory Approach**

Suppose the strategy space of the game is convex and all payo ﬀ functions are quasiconcave. Then, if (−1) n | H | is positive whenever ∂π i /∂x i = 0, all i, there is a unique NE.

## Multiple Equilibrium

The problem with mulitple equilibria is that the players may not know which equilibirum will prevail. Hence, it is entirely possible that a nonequilibrium outcome results because one player plays one equilibrium strategy while a second player chooses a strategy associated with another equilibrium. 

An alternative method to rule out some equilibria is to focus only on the Pareto optimal equilibrium, of which there may be only one.

## Comparative Statics

It explores how changes in the parameters of a game influence the strategies and outcomes of the game. This analysis helps to understand the sensitivity of the equilibrium strategies and outcomes to changes in external factors like costs, market demand, regulations, etc. 

**Implicit Function Theorem Approach**: by analizing the derivatives of the qeuilibrium strategies with respect to the parameters.

**Supermodular Games Approach**: given the condition that games are supermodular, if the second partial derivative of the payoff function w.r.t. strategy $x_i$ and parameter $a$ is non-negative for all players, then both the largest and smallest NE strategies are increasing functions of parameter a.

# Dynamic Game Setting

Previous games are static, which mean all decision are made at the same. However, dynamic model means decisions are made over time.

## Stackelberg Game

Two roles: leader and follower. 

In SCM models, large firms are leaders and small firms are followers.

Intution of two roles:

1. Follower's strategy will be the best response to any decision made by the leader.
2. The leader has the above information and will select the best response strategy anticipating the strategy by the follower.

## Repeated & Stochastic Simultaneous Moves

Inventory models used in SCM literature often involve inventory replenishment decisions that are made over and over again.

**Memoryless:** then it's a repeated game.

More common it's the time dependent game, because there is some transfer of inventory and/or backorders between periods.

A good feature of repeated game is that players may employ trigger strategies: This threat of reverting to a diﬀerent strategy may even induce players to achieve the best possible outcome.

A typical time dependent game is the **stochastic game/Markov game.** And a standard simplifying assumption that demands are i.i.d across periods.

## Differential Games

Differential games are the extension of the multiple periods games, however, the time is continuous.

In such game setting, factors like price are note changed instantaneous. Thus, the model requires differential equations to describe the rate of change of those variables over time. That's where the name "differential" comes from.

**Open Loop Strategies**

Strategies are predetermined at the begining of the game and do not change in response to the environment and the states of other players.

In a supply chain context, an open loop strategy could be a manufacturer deciding in advance how mmuch of a product to produce each month. They have signed the order and will fulfill it regardless of what happens during the month.

**Closed Loop Strategies**

Strategies adapt to chages in the game environment as well as other players states. in a supply chain context, a retailer might adjust inventory levels and prices based on the sales data and stock levels updated in real time.



# Cooperative Games

## Game Setting

The game consists of the set of $N$ players with coaliations $S \sube N$ and a characteristic function $v(S)$ that specifies a value that create by any subset of players in $N$. It's assumed that players are free to form any coalitions beneficial to them.

**Definition: Core of the game**

The unility vector $\pi_1, ..., \pi_N$ is in the cores of the cooperative game if everyone gets at least what they would have if htey worked alone or with any other group.

$\forall S \subseteq N, \sum_{i \in S} \pi_i \geq v(S) and \sum_{i \in N} \pi_i \geq v(N). $

The core of the game may not exist and could also be not unique.

## Shapley Value

The Shapley value suggests a fair way to distribute the total reward among participants based on their individual contributions.

- Summation is a sum over all subsets of players that do not include player i.
- $|S|!$ is the number of different ways member of subset players can come together. $(N-|S| = 1)$ is the number of players not in the subset before player i joins. $N!$ is total number of ways all players can come together. This fraction is the probability that describes subset S occurs in all possible orderings.
- The right term is the marginal contribution of player i to the subset S

Putting it together, it's the expected contribution across all possible ways play i could join the group.

## Biform Games

It's a combination of cooperative and non-cooperate games. 

- The cooperative stage: players negotiate and form coalition. 
- The non-cooperative stage: making individual decision to maximize their own utility.

The game begins by players making choices from among their strategies and incurring costs. After that, a cooperative game occurs in which the characteristic value function depends on the chosen actions.

When the company is purchasing, it needs to choose which vendors to buy from. This is to form a coalition with the suppliers, it could be cooperative. Once the company chooses the vendors, it must maximize the outcome within the limits of the earlier choice.

# Imperfect Information Games

The previous games assume players have the same information, for example, other players' strategy. One ﬁrm may have a better forecast of demand than another ﬁrm, or a ﬁrm may possess superior information regarding its own costs and operating procedures. Furthermore, a ﬁrm may know that another ﬁrm may have better information, and, therefore, choose actions that acknowledge this information shortcoming.

## Signaling Game

A two-player example:

Imagine a chef (the manufacturer) who is planning to host a big dinner party (produce products) and needs to order ingredients (capacity) from a supplier. The chef has a better idea than the supplier about how many guests (demand) will likely attend but knows that more ingredients allow for more flexibility in case of extra guests. However, more ingredients also mean higher costs, which the supplier must bear.convincing.

- **Pooling Equilibrium:** The chef gives the same guest estimate regardless of the actual number expected. Consequently, the supplier can’t tell whether the party is really big or small and might overprepare (more ingredients) or underprepare (fewer ingredients).
- **Separating Equilibrium (Signaling):** The chef uses different estimates or signals based on the actual number of expected guests. If the chef can convincingly use a specific signal for a big party (like a higher payment guarantee or special conditions that only make sense with more guests), the supplier can trust the estimate and provide the right amount of ingredients.

The key in these types of games is communication and trust, backed by actions that align with the true situation. Signals must be carefully chosen so they’re believable and align with the interests of both parties, ensuring efficient and effective collaboration.

## Screening

**Game Setting:** The less-informed party designs a set of choices aimed at including informed party to reveal their private information through their choices.

**SCM model:** A supplier offers a manufacturer a menu of contracts, each for a specific type of manufacturers. Volume Discount Contract: lower per-unit price but requires high minimum purchase.Flexible Purchase Contract: higher per-unit price but allows smaller order quantities.

## Bayesian Games