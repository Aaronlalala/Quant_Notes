# Question 1

You have a large jar containing 999 fair pennies and one two- headed penny. Suppose you pick one coin out of the jar and flip it 10 times and get all heads. What is the probability that the coin you chose is the two-headed one?

Define two events:

- A:  Two headed coin is selected.
- B: 10 tosses are heads.

The formula for conditional probability is:

$$
P(A | B) = \frac{P(A \cap B)}{P(B)}
$$

It can also be expressed as:

$$
P(A | B) = \frac{P(B | A) \cdot P(A)}{P(B)}
$$

$$
P(A | B) = \frac{P(B | A) \cdot P(A)}{P(B | A^c) + P(B | A)}\\
P(A|B) = \frac{1\cdot 1/1000}{1/1000 + 999/1000 \cdot 1/1024} \approx \frac{1}{2}
$$

# Question 2

A person claims he could distinguish the color of M&M chocolate beans by tasting them. There are 5 colors of chocolate beans in total, he tasted 3 and got two correct. What could you say about his claim? What about 100 beans and getting 30 correct?

If the person only tastes 3 beans in total, the number of sample size does not satisfy to use central limit theorem. Let the test statistics be number of success, $t = 2$. And $t$ follows binomial distribution.

P-value = $P(t \geq 2) = \binom{3}{2} 0.2^2 \cdot 0.8^1 + \binom{3}{3} 0.2^3 = 0.104$

We have 90% confidence to reject the null hypothesis.

However, as the person tastes 100, we could use CLT to construct test statistic.

Let $t = \frac{\overline{X} - \mu}{\frac{\sigma}{\sqrt{n}}}$ and it follows standard normal distribution $N(0,1)$

P-value = $P\left(t \geq \dfrac{0.3 - 0.2}{\frac{100*0.8*0.2}{\sqrt{100}}}\right) = P\left(t \geq \frac{0.1}{1.6} \right) = 0.0625$

$P\left(t \geq 0.0625 \right) \approx 0.475$, fail to reject the null hypothesis.
