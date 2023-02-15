[toc]

# Calculus

**Integral by parts:** $\int fg' = f\cdot g - \int f'g$.

**Integrate exponential function:** try to compose probability density function of Gaussian.

## Taylor Series

Taylor Series general form: $f(x) = \sum_{n=0}^{\infty}\dfrac{f^{(n)}(a)}{n!}(x-a)^n$.

When $a=0$ it could be simplified as $f(x) = \sum_{n=0}^{\infty}\dfrac{f^{(n)}(0)}{n!}x^n$. 



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

## Singular Value Decomposition

Suppose A is invertible, singular values of A are reciprocal of singular values of $A^{-1}$. $A = U\Sigma V^T \implies A^{-1} = V\Sigma^{-1}U^T$. Due to the property of diagonal matrix inversion, the diagonal terms which are singular values of $A^{-1}$ are reciprocal of singular value of A.



