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


