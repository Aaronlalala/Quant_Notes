[toc]

# Calculus

**Integral by parts:** $\int fg' = f\cdot g - \int f'g$.

**Integrate exponential function:** try to compose probability density function of Gaussian.

## Taylor Series

Taylor Series general form: $f(x) = \sum_{n=0}^{\infin}\dfrac{f^{(n)}(a)}{n!}(x-a)^n$.

When $a=0$ it could be simplified as $f(x) = \sum_{n=0}^{\infin}\dfrac{f^{(n)}(0)}{n!}x^n$. 

# Linear Algebra

## Linearly Independent

Vectors are linearly independent when linear combination of vectors is 0 if and only if all parameters are zero.

## Orthogonal Matrix

An orthogonal matrix is a square matrix whose columns are mutually orthogonal unit vectors and the dot product of the columns equal to zero.

Some properties of orthogonal matrix:

- It must be square matrix
- Columns of an orthogonal matrix are mutually orthogonal and has length 1.
- $A^TA = I$
- It preserves inner product: $<Av, Aq> = (Av)^T (Aq) = v^T (A^T A) q = v^T I q = v^T q = <v, q>$
- It preserves the length of vectors: $||Av|| = ||v||$.

#### Orthogonal Vector

Two vector are orthogonal if their inner product is zero. Projection of one onto the other is zero. If vectors are orthogonal. They are linearly independent.

## Matrix Condition Number

The condition number of a matrix is a measure of the sensitivity of the solution of a linear system to small perturbations in the data. A high condition number indicates the solutionis hightly sensitive to small perturbations in the data.

$$\kappa(A) = \|A\|_2 \|A^{-1}\|_2 = \frac{\sigma_{\max}(A)}{\sigma_{\min}(A)}$$, where $\sigma$ denotes the singular value of matrix A. 

### Perturbation to the output coefficient

It also provides a **upper bound** for the relative error $\frac{
|\delta_x|}{|x|}$. Define error of solution $\delta_x = \hat{x} - x$, where $\hat{x}$ is the  estimated solution. This solution not equals to x due to perturbations of b. $A\hat{x} = b + \delta_b$.  Then we have $A\hat{x} = A(x + \delta_x) = Ax + A\delta_x = b + \delta_b \implies A\delta_x = \delta_b \implies \delta_x = A^{-1}\delta_b$. Take the norm at both sides, we have $\|\delta_x\| = \|A^{-1}\delta_b\| \leq \|A^{-1}\|\|\delta_b\|$. Use similar method, we have $\|b\| \leq \|A\|\|x\| \implies \|x\| \geq \|b\| / \|A\|$. Divide two norms $\frac{\|\delta_x\|}{\|x\|} \leq \|A\|\|A^{-1}\|\frac{\|\delta_b\|}{\|b\|}$. 

### Perturbation to the input coefficient



## Matrix Norm

$\|A\|$ is the matrix norm, which maps a matrix to a scalar and satisfies certain properties including, positive, homogeneous, and submultiplicative. Without explicit subscript, it's 2-norm by default.



## Complexity to Solve a Linear System

orthogonal:

Triangular:

### LU Decomposition

Partial Pivoting

