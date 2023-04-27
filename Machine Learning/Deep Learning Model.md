# Perceptron Algorithm

[Very good explanation video](https://www.youtube.com/watch?v=4Gac5I64LM4)

It's a basic unit of a neural network. It assumes observations are linear separable. For a specific observation, $y = w_0 + w_1x_1 + w_2x_2 +...+ w_dx_d = w^tx$, where the first element of $x$ is 1. If $y > t$, then it's classified as class 1. Otherwise, it's classified as class 2 (Binary classification and t = 0 as default).

Update parameters: $w = w + \alpha x_i\cdot I$, where $I$ is an indicator function. $I = 1$ when the observation actually belongs to class 1.$\alpha$ is the learning rate.







ReLU Function

