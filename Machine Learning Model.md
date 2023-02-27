[toc]



# Linear Model

## Linear Regression







## Logistic Regression

$\hat{y} = sigmoid(w^Tx + b)$. The sigmoid function is to make the estimated value's range is 0 to 1 to represent the probability. The learning process is to find out optimal parameter $w$.

**Sigmoid function** $\sigma(x) = \frac{1}{1 + e^{-x}}$. 

**Loss (error) function (apply to single observation):** in losgistic regression, its loss function is not $\frac{1}{2}(\hat y-y)^2 $ because this loss function is not convex and cannot be easily optimized. The convex loss function that this model uses is $L(\hat{y}, y) = -(y\cdot log\hat{y} + (1-y)\cdot log(1-\hat{y}))$.

**Cost function (average loss for entire training set):** $J(w, b) = \dfrac{1}{m}\sum L(\hat{y}^{(i)}- y^{(i)})^2$

**class_weight:** A very interesting parameter of the model. It describes the cost for making a false prediction for the label. Sometimes making a false prediction for a positive target is much larger than a false prediction for a negative target.



## Polynomial Regression

Regularization?



# Classification Tree

Genearlly, classification tree divides the feature space into rectangular regions.

## Decision Tree (non-parametric model)

Decision tree prefer categoricald data than continuous numerical data.

### Maximum depth of the tree

Can maximum depth of a decision tree be greater than the number of the features? In most cases, yes. Because, if there are continuous features, then it could be divided into many bins to make decisions. In addition, categorical features may also have more than two category. It also provides more combinations for making decisions.

### Information Gain

**In classification model:** $IG(f, sp) = I(parent) - (\frac{N_L}{N}I(left) + \frac{N_R}{N}I(right))$, where function $I$ is the criteria to measure the **impurity** of a node. There mare many metrics for impurity, for example gini index and entropy.  The learning process will recursively split the data into children nodes until the information gain is 0 (cannot make the sample in children more pure).

**In decision tree regression model:** the impurity of a node is $I(node) = MSE(node) = \frac{1}{N}\sum(y^{(i)} - \bar{y})^2$, $\bar{y}$ is the mean target value of all sample in that node.



# Instance Based Classifiers

## K Nearest Neighbor (KNN)

KNN is an instance based model, it's also called lazy learning model. Because it does not learning a disriminative function from the training data but recording the traning data.





# Unsupervised Model

## Principal Components Analysis

PCA is an orthogonal linear transformation that transforms the data to a new coordinate to maximize the variance of projection on axes. 



The eigenvectors of the covariance matrix represent the principal components (the 
their magnitude. I

### Drawbacks of PCA

- PCA is sensitive to scale of features, because the optimization process mesures the variance of projection.
- Sometimes, it's hard to find the interpretation of principal components especially after scalling.

## Linear Discriminant Analysis

LDA takes advantages of the label. It tries to find a projection (a direction) that maximize the distance groups while minimize the variance within groups. In two dimension situations, the objective function is $max \frac{(\mu_1 - \mu_2)^2}{\sigma_1^2 + \sigma_2^2}$.

Assumption: it assumes that all groups of data are in normal distribution.

## What is the difference between Linear Discriminant Analysis and PCA?

One significant difference is that PCA does not require knowledge of labels, but LDA utilize the Information of label.

**Is there any cases LDA outperforms PCA?**

Yes. There are some cases when projection direction that maximizes the variance cannot linearly separate data. For example, 

<img src="Figures/LDA outperforms PCA.jpeg" alt="LDA outperforms PCA" style="zoom:20%;" />

If we have no information of data, we certainly cannot assure that data come from different distribution, (if their means are close to each other). Thus, we cannot separate two groups of data. That's not the fault of PCA. However, if we have the oracle, we can certainly find the direction that orthogonal to the covariance direction, to linearly separate two groups of data. However, PCA cannot take the advantage of oracle, still project data to the direction that maximize the variance.

