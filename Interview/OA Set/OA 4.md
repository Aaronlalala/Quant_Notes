# Question 1

Given a two-dimensional  joint distribution:

$f_{XY}(x, y) = \dfrac{e^{-y/x}e^{-x}}{x}$, where $x > 0, y > 0$. Otherwise, $f= 0$. Find the probability $P(Y >1 | X = x)$. 

**Answer:**

Use the formula of conditional probability the probablity is the integral of the joint distribution on the desired range of Y over the marginal distribution of X. 

$P(Y >1 | X = x) = \dfrac{\int_1^{\infty}f(x, y)dy}{\int_0^{\infty}f(x, y)dy} = \dfrac{e^{-\frac{1}{x}}e^{-x}}{e^{-x}} = e^{-\frac{1}{x}}$.

# Question 2

A card is selected at random from a standard pack of 52 playing cards. A standard deck contains 13 hearts and 12 face cards, 3 of each suit. Define two events, A: a heart is chosen; B: a face card is chosen. What is the value of $P(A \cup B)$?

**Answer:**

$P(A\cup B) = P(A) + P(B) - P(A \cap B) = \frac{13}{52} + \frac{12}{52} - \frac{3}{52}=\frac{22}{52}$. 

# Question 3

One out of four statements a child makes is a lie. There are 6 cards numbered 1 through 6. If the child picks a card, what is the probability that the child truthfully says the card number is 5?

**Answer:**

Define event A: child tells the truth and event B: the card is number 5.

$P(A \cap B) = P(A|B) P(B) = \dfrac{3}{4}*\dfrac{1}{6} = \dfrac{1}{8}$

# Question 4

Let X be distributed as $f(x) = e^{-(x-A)}$, where $X>A, A>0$. Otherwise, $f(x) = 0$. During the experiment, you observed 3 different values of X: 9, 10, and 11. Find an estimate of A using the Method of Moment (using the first moment). 

**Answer:**

The sample first moment (sample mean) is 10. The theoretical moments of the distribution is the mean of the distribution, which is (1 + A). It's exponential distribution shifted right by A. Thus, solve $1 + A = 10$, we have $A = 9$.
