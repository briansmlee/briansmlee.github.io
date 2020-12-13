---
layout: page
title: 4.3 Linear Discriminant Analysis - Exercises
permalink: /esl/04_03_Exercises/
chapter_title: 4 Linear Methods for Classification
section_title: 4.3 Linear Discriminant Analysis
type: Exercises
usemathjax: true
---

* toc
{:toc}

### 4.1

See [this Khan Academy post](https://www.khanacademy.org/math/multivariable-calculus/applications-of-multivariable-derivatives/constrained-optimization/a/lagrange-multipliers-examples) on using Lagrange multipliers. To find $a$ that maximizes $a^T B a$ subject to $a^T W a = 1$, we can find the critical points of the Lagrange function, $L(a, \lambda) = a^T B a - \lambda (a^T W a - 1)$.

Critical points of $L$ satisfy $ \frac{\partial L}{\partial a} = 2 B a - 2 \lambda W a = \mathbf{0}$ (and $ \frac{\partial}{\partial \lambda} = a^T W a - 1 = 0$, the original constraint). Rearranging terms, we obtain a [generalized eigenvalue problem](https://en.wikipedia.org/wiki/Eigendecomposition_of_a_matrix#Generalized_eigenvalue_problem), $ Ba = \lambda Wa$. If $W$ is invertible, this can be transformed to a standard eigenvalue problem, $W^{-1}Ba = \lambda a$. 

Among the eigenvectors of $W^{-1}B$, which one maximizes $a^T B a$? By left-multiplying $a^T$ to the generalized eigenvalue problem, we obtain $a^T B a = \lambda a^T W a = \lambda$. So, pick the eigenvector with the largest eigenvalue.

### 4.2

*Please see the problem statement in the book.*

(a) Follows from rearranging terms in $\hat{\delta}\_2(x) > \hat{\delta}\_1(x)$ using LDA discriminant functions from (4.10).

(b) Let's obtain the normal equations for (4.55) w.r.t. $\beta$ and show that it is equivalent to (4.56).

We can rewrite (4.55) as $RSS = \lVert y_i - \mathbf{1} \beta_0 - X \beta \rVert^2$.

Then $\frac{d}{d \beta_0} RSS = \frac{d}{d \beta_0} - 2 \beta_0 \mathbf{1}^T y - 2 \beta_0 \mathbf{1}^T X\beta + \beta_0^2 \mathbf{1}^T \mathbf{1} = - 2 \mathbf{1}^T y + 2 \mathbf{1}^T X \beta + 2N \beta_0$. Hence $N \beta_0 = \mathbf{1}^T y - \mathbf{1}^T X \beta$.

Since $\frac{\partial}{\partial \beta} RSS$ gives $X^TX \beta = X^T(y - \mathbf{1} \beta_0)$, we substitute $\beta_0$ from above to obtain

$$ X^TX \beta = X^Ty - \frac{1}{N} X^T \mathbf{1}\mathbf{1}^T y + \frac{1}{N} X^T \mathbf{1}\mathbf{1}^T X\beta $$

By letting $C$ be the [centering matrix](https://en.wikipedia.org/wiki/Centering_matrix) $I - \frac{1}{N} \mathbf{1}\mathbf{1}^T$, we obtain:

$$ X^T C X \beta = X^T C y $$

Let's show that above is equivalent to (4.56). 

**RHS**: Note that $Cy = y$ because the mean $\overline{y}$ that centering matrix subtracts from each $y_i$ is $N_1 \cdot - \frac{N}{N1} + N_2 \cdot \frac{N}{N2} = 0$. Then, $X^TCy$ is equal to $N (\hat{\mu}\_1 - \hat{\mu}\_2)$ because:

$$ N (\hat{\mu}_1 - \hat{\mu}_2) = - \frac{N}{N_1} \sum_{g_i = 1} x_i + \frac{N}{N_2} \sum_{g_i = 2} x_i = \sum_{g_i = 1} y_i x_i + \sum_{g_i = 2} y_i x_i = X^T y = X^T C y$$

**LHS**: Similarly, $CX$ centers each column/feature of $X$. So, $i$-th row of $CX$ is $x_i - \frac{N_1}{N} \hat{\mu}\_1 - \frac{N_2}{N} \hat{\mu}\_2$.

Then, view $X^T CX = (X^T){(CX)^T}^T$ as sum of outer products, $\sum_i x_i (x_i - \frac{N_1}{N} \hat{\mu}\_1 - \frac{N_2}{N} \hat{\mu}\_2)^T$, which becomes

$$ \begin{align*}
X^T CX 
&= \sum_i x_i (x_i - \frac{N_1}{N} \hat{\mu}_1 - \frac{N_2}{N} \hat{\mu}_2)^T\\
&= \sum_i x_i x_i^T - \sum_{g_i = 1} \frac{N_1}{N} x_i \hat{\mu}_1^T - \sum_{g_i = 2} \frac{N_1}{N} x_i \hat{\mu}_1^T - \sum_{g_i = 1} \frac{N_2}{N} x_i \hat{\mu}_2^T - \sum_{g_i = 2} \frac{N_2}{N} x_i \hat{\mu}_2^T \\
&= \sum_i x_i x_i^T - \frac{N_1^2}{N} \hat{\mu}_1 \hat{\mu}_1^T - \frac{N_2^2}{N} \hat{\mu}_2 \hat{\mu}_2^T - \frac{2 N_1 N_2}{N} \hat{\mu}_1 \hat{\mu}_2^T \\
\end{align*} $$

due to $[\sum_{g_i = 1} x_i] \hat{\mu}\_1^T = N_1 \hat{\mu}\_1 \hat{\mu}\_1^T$ and its variations. The LHS of (4.56) also reduces to:

$$ \begin{align*}
(N - 2) \hat{\Sigma} + N \hat{\Sigma}_B 
&= \sum_{g_i = 1} (x_i - \hat{\mu}_1) (x_i - \hat{\mu}_1)^T + \sum_{g_i = 2} (x_i - \hat{\mu}_2) (x_i - \hat{\mu}_2)^T + \frac{N_1 N_2}{N} (\hat{\mu}_2 - \hat{\mu}_1) (\hat{\mu}_2 - \hat{\mu}_1)^T \\
&= \sum_{i} x_i x_i^T - N_1 \hat{\mu}_1 \hat{\mu}_1^T - N_2 \hat{\mu}_2 \hat{\mu}_2^T + \frac{N_1 N_2}{N} (\hat{\mu}_2 \hat{\mu}_2^T - 2 \hat{\mu}_1 \hat{\mu}_2^T + \hat{\mu}_1 \hat{\mu}_1^T)
\end{align*} $$

which is equivalent to $X^TCX$ above because $\frac{N_1 N_2}{N} - N_1 = \frac{N_1 (N_2 - N)}{N} = - \frac{N_1^2}{N}$.

(c) $\hat{\Sigma}\_B \beta$ is in the direction of $(\hat{\mu}\_2 - \hat{\mu}\_1)$ because $(\hat{\mu}\_2 - \hat{\mu}\_1)^T \beta$ in $\hat{\Sigma}\_B \beta$ is a scalar. (4.57) follows from moving $\hat{\Sigma}\_B \beta$ to RHS and rearranging the terms.

(d)

(e)

### 4.3


### 4.8

### 4.9