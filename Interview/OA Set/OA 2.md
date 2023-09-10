# Question 1: Matrix multiplication

<img src="../../Figures/OA 2.1.png" alt="OA 2.1" style="zoom:20%;" />

# Question 2

We play a game with two tetrahedral dice (four-sided), red and blue, each with faces labeled 1-4. In each turn, you simultaneously roll both dice. If the blue shows more than the red, you are paid the difference, otherwise paid nothing. If the blue and red show the same value, the game is immediately over, otherwise, you take another turn. What is the fair value of the game?

This game could be divided into binary situations, whether game ends or not. There are 16 outcomes of rolling two dice. The probability of game ends is $P_{end} = \dfrac{4}{16} = \dfrac{1}{4}$. The probability of game does not end is $P = \frac{12}{16} = \frac{3}{4}$. Given the game does not end, there are 12 outcomes, half of them generate positive gain. The expected return is $\dfrac{1}{12} (1 + 2 + 3 + 1 + 2 + 1) = \dfrac{10}{12} = \dfrac{5}{6}$. 

Then there are two methods to solve the fair value.

## Method 1: Inifite Geometric Series

**A common mistake**

Let $N$ be the number of rounds that generates gain. $P(N = 1) = \frac{3}{4}$, $P(N = 2) = \frac{3}{4}^2$, $P(N = n) = (\frac{3}{4})^n$. Since each round generates the same gain, we only need to compute the expected number of rounds, due to the linearity of the expectation, we could solve the expected value of the game. 

Comment: in the above approach, $P(N=1) = \frac{3}{4}$ implies that with a probability of $\frac{3}{4}$, the game will end after 1 round of gaining. However, that is not true according to the setup, you gain $\frac{5}{6}$ will automatically allows you enter to the next round. It does not end. Let $N$ be the number of rounds that generates gain. $P(N = 1) = \frac{3}{4}\cdot\frac{1}{4}$, $P(N = 2) = \frac{3}{4}^2\cdot\frac{1}{4}$, $P(N = n) = (\frac{3}{4})^n\cdot\frac{1}{4}$.  You should add the probability that it ends at the next round. Expectec value is $\dfrac{1 \cdot 3}{4 \cdot 4}\left(1+2\left(\frac{3}{4}\right)+3\left(\frac{3}{4}\right)^2+\ldots\right)$This series sum up to 3 (There is a formula to compute this, and I verify with the code). The fair value is $3 \cdot \frac{5}{6} = 2.5$. 

**Another easier way to use geometric series**

In the game, each round you have probability of $\frac{3}{4}$ to gain $\frac{5}{6}$ and enter to the next round. There is a probability $\dfrac{3}{4}$ to gain $\dfrac{5}{6}$ in the round 1. There is a probability of $\frac{3}{4}^2$ to gain $\frac{6}{5}$ in the round two. Thus, $E = \dfrac{5}{6} (\frac{3}{4} + \frac{3}{4}^2 + \frac{3}{4}^3 + ...) = \dfrac{5}{6} \cdot \dfrac{\frac{3}{4}(1 - \frac{3}{4}^n)}{1 - \frac{3}{4}} = \dfrac{5}{6} \cdot \dfrac{3/4}{1/4} = 2.5$

## Method 2: Recursion

In each game, there are only two outcomes, end or continue. If given the game is continue, the future states are independent with previous states. Thus, the actual gain is not $\dfrac{5}{6}$, but $\dfrac{5}{6}$ plus the fair value of the game. Since it gives us another chance to play this game. We have the following recursion formula:

$E = \dfrac{1}{4} \cdot0 + \dfrac{3}{4}\cdot(\dfrac{5}{6} + E)$. Solve this equation, we have $E = 2.5$

This method is much easier in computation, but requires more thinking.





