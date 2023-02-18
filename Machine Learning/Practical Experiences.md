# Model Selection

When dealing with the traditional tabular data machine learning, choosing a linear or non-linear model is a very first dealing thing. 

**Check the correlation:** this is a very easy way to have a first glance of the relationship of features and response. If the correlation is really low, it means they have pretty low linear relationship. Then probably choose non-linear model.



# Metrics

## Accuracy v.s. Area Under Curve (AUC)



# Feature Engineering

## Feature Scaling

Feature scaling is a method used to normalize the **range of** independent variables or features. It's also known as data normalization.

Should use feature scalling with the following three situations:

1. Use distance-based model. (e.g. KNN)
2. Model using Gradient Descent optimization. (e.g. linear regression)
3. If regularization is applied. Otherwise, coefficients cannot be penalized appropriately.

One thing to note is that scaling is not converting a smaple to normal distribution. If we want to do this, we need to use inverse of inverse transformation.

**Do we scale the target value?**

$w_{t+1} = w_t - \gamma \nabla_w l(f_s(x), y)$, where $l$ is loss function, $f$ is function of parameters and $y$ is the target value. The optimization process depends on the shape (property) of parameter function $f$. Scaling the target value will not affect the speed of convergence. ([Link](https://stats.stackexchange.com/questions/111467/is-it-necessary-to-scale-the-target-value-in-addition-to-scaling-features-for-re))

**What if we use regularized model?**

If we don't scale the response while scaling the independent variables, the parameters might become really large. Will it affect the performance of regularization? But one thing can almost sure is that calculation will generate much more rounding error. (from numerical analysis prospective)
