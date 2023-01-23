[toc]



# Linear Model

## Regression

### Linear Regression

### Logistic Regression

### Polynomial Regression

Regularization?



# Classification Tree

Genearlly, classification tree divides the feature space into rectangular regions.

## Decision Tree

### Maximum depth of the tree

Can maximum depth of a decision tree be greater than the number of the features? In most cases, yes. Because, if there are continuous features, then it could be divided into many bins to make decisions. In addition, categorical features may also have more than two category. It also provides more combinations for making decisions.

### Information Gain

**In classification model:** $IG(f, sp) = I(parent) - (\frac{N_L}{N}I(left) + \frac{N_R}{N}I(right))$, where function $I$ is the criteria to measure the **impurity** of a node. There mare many metrics for impurity, for example gini index and entropy.  The learning process will recursively split the data into children nodes until the information gain is 0 (cannot make the sample in children more pure).

**In decision tree regression model:** the impurity of a node is $I(node) = MSE(node) = \frac{1}{N}\sum(y^{(i)} - \bar{y})^2$, $\bar{y}$ is the mean target value of all sample in that node.





