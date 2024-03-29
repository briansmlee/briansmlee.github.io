---
layout: page
title: 3.2 Linear Regression Models and Least Squares - Derivations
permalink: /esl/03_02_Derivations/
chapter_title: 3 Linear Methods for Regression
section_title: 3.2 Linear Regression Models and Least Squares
type: Derivations
usemathjax: true
---

* toc
{:toc}

### (3.2) RSS criterion is "statistically reasonable" if $y_i$'s are conditionally independent given X

### (3.4) Differentiate RSS$(\beta)$

RSS$(\beta)$ $ = y^T y - 2 \beta^T X^T y + \beta^T X^TX \beta$. Note $\frac{\partial}{\partial \beta} \beta^T X^T y = X^Ty$. Show $ \frac{\partial}{\partial \beta} \beta^T X^T X \beta = 2 X^T X\beta$. 

Let $ X^T X = A$. Then $\beta^T A \beta = \sum_i \beta_i (A\beta)\_{i} = \sum_i \beta_i \sum_j A_{i,j} \beta_j$. Reorder to $\sum_i \sum_j A_{i,j} \beta_i \beta_j$. Then:

$$ \begin{align*}
\frac{d}{d \beta_k} \sum_i \sum_j A_{i,j} \beta_i \beta_j 
&= \frac{d}{d \beta_k} [A_{k,k}{\beta_k}^2 + \sum_{i \neq k} A_{i, k} \beta_i \beta_k + \sum_{j \neq k} A_{k, j} \beta_k \beta_j] \\
&= 2 A_{k,k} {\beta_k} + \sum_{i \neq k}^d A_{i, k} \beta_i + \sum_{j \neq k}^d A_{k, j} \beta_j \\
&= \sum_{i}^d A_{i, k} \beta_i + \sum_{j}^d A_{k, j} \beta_j \\
&= (A \beta)_{k} + (A^T \beta)_{k} \\
&= ((A + A^T)\beta)_{k} \\
\end{align*} $$

Therefore, $\frac{\partial}{\partial \beta} \beta^T A \beta = (A^T + A)\beta$, equivalent to $2 X^T X\beta$ since $X^T X$ is symmetric.

From the two derivatives, we obtain $ \frac{\partial}{\partial \beta} RSS = - 2 X^T (y - X \beta)$, which we set to zeros for the normal equation.

Reference:
* Barnes. [*Matrix Calculus*](https://atmos.washington.edu/~dennis/MatrixCalculus.pdf). Section 5.

### (3.8) Covariance matrix of OLS estimate

Note $Var(\hat{\beta}) 
= E[(\hat{\beta} - E[\hat{\beta}])(\hat{\beta} - E[\hat{\beta}])^T]
= E[\hat{\beta}\hat{\beta}^T] - E[\hat{\beta}]E[\hat{\beta}]^T$. 
Equivalently, $E[yy^T] = Var(y) + E[y]E[y]^T$.

$$ \begin{align*}
Var(\hat{\beta}) &= E[\hat{\beta}\hat{\beta}^T] - E[\hat{\beta}]E[\hat{\beta}]^T\\
&= E[(X^TX)^{-1}X^Tyy^TX(X^TX)^{-T}] - E[(X^TX)^{-1}X^Ty]E[(X^TX)^{-1}X^Ty]^T\\
&= (X^TX)^{-1}X^TE[yy^T]X(X^TX)^{-1} - (X^TX)^{-1}X^TE[y]((X^TX)^{-1}X^TE[y])^T\\
&= (X^TX)^{-1}X^T(\sigma^2I + E[y]E[y]^T)X(X^TX)^{-1} - (X^TX)^{-1}X^TE[y]E[y]^TX(X^TX)^{-1}\\
&= (\sigma^2(X^TX)^{-1} + (X^TX)^{-1}X^TE[y]E[y]^TX(X^TX)^{-1}) - (X^TX)^{-1}X^TE[y]E[y]^TX(X^TX)^{-1}\\
&= \sigma^2(X^TX)^{-1}
\end{align*} $$

Reference: 
* Paisley. [*ColumbiaX - CSMM.102x: Machine Learning*](https://www.edx.org/course/machine-learning). Lecture 3.

### (3.8) Estimate $\hat{\sigma}^2$ of $y_i$'s variance using denominator $N-p-1$ is unbiased

See [this StackExchange answer](https://math.stackexchange.com/a/2342977/455856). Note that this answer assumes that the variance $\sigma^2$ of $y_i$ comes from $\varepsilon \sim N(0, \sigma^2)$.

TODO: Is it possible to derive without the assumption above?

### (3.10) OLS estimate has normal distribution under (3.9)

Let $e$ be the N x 1 vector of errors $\varepsilon$ from (3.9). Assuming errors are i.i.d., $e \sim N(0, \sigma^2 I)$.

Note $\hat{\beta} = (X^TX)^{-1}X^Ty = (X^TX)^{-1}X^T(X\beta + e) = \beta + (X^TX)^{-1}X^Te$.

If $x \sim N(\mu, \Sigma)$ then $\beta + a^Tx \sim N(\beta + a^T\mu, a^T\Sigma a)$. So, covariance matrix of $\beta + (X^TX)^{-1}X^Te$ is $(X^TX)^{-1}X^T \sigma^2 I X (X^TX)^{-1} = \sigma^2 (X^TX)^{-1}$, which confirms our derivation from (3.8).

Hence, $\hat{\beta} \sim N(\beta, \sigma^2 (X^TX)^{-1})$.

### (3.11) $(N-p-1)\hat{\sigma}^2$ has chi-squared distribution

See [this StackExchange answer](https://stats.stackexchange.com/a/20230/261782). Below slightly modifies the answer by using (imo) a bit easier linear algebra.

From (3.8), $(N - p - 1)\hat{\sigma}^2 = \sum_i^N (y_i - \hat{y_i})^2 = \lVert y - \hat{y} \rVert^2$.

$y - \hat{y} = (X\beta + \varepsilon) - X(X^TX)^{-1}X^T(X\beta + \varepsilon) = \varepsilon - X(X^TX)^{-1}X^T\varepsilon = (I - H)\varepsilon$, where H is projection/hat matrix.

Let $A = I - H$, which satisfies:
1. $A^T = A$. Symmetric matrix has $N$ real eigenvalues.
2. $A^2 = A$. The $N$ eigenvalues are $0$ or $1$ since $\lambda v = Av = A^2v = \lambda^2 v$.
3. $tr(I - H) = N - tr(X(X^TX)^{-1}X^T) = N - tr(X^TX(X^TX)^{-1}) = N - (p + 1)$. Since the trace equals the sum of eigenvalues, $N - p - 1$ eigenvalues are 1.

So, we can eigen-decompose $A = Q \Lambda Q^{-1}$ where $\Lambda = diag(\underbrace{1,...,1}\_{N-p-1}, \underbrace{0,...,0}\_{p+1})$.

From $\varepsilon \sim N(0, \sigma^2 I)$ we obtain 
$A\varepsilon \sim N(0, \sigma^2A)$ because $A\sigma^2 I A^T = \sigma^2A$.\\
Moreover, $Q^TA\varepsilon \sim N(0, \sigma^2 \Lambda)$ because $Q^TAQ = Q^T(Q \Lambda Q^{-1})Q = \Lambda$.

That is, among N independent random variables in $Q^TA\varepsilon$, first $N - p - 1$ have variance $\sigma^2$ and others are fixed at 0 (both mean and variance are 0). Then, $(Q^TA\varepsilon)\_i / \sigma^2$ are independent standard normals for all $i$ upto $N-p-1$. So, $\chi_{N-p-1}^2 = \sum_{i=1}^{N-p-1} (Q^TA\varepsilon)\_i^2 / \sigma^2$, but we can extend the sum upto $N$ since remaining $p+1$ entries are fixed at 0.

Therefore, $\sigma^2 \chi_{N-p-1}^2 = (Q^TA\varepsilon)^T (Q^TA\varepsilon) 
= \varepsilon^TA^TA\varepsilon 
= \lVert (I - H)\varepsilon \rVert^2
= \lVert y - \hat{y} \rVert^2
= (N - p - 1)\hat{\sigma}^2$.

Alternatively, we can use the following theorems:
* If A is a projection matrix with rank $r$ and $z \sim N(0, I)$, then the quadratic form $z^TAz$ is distributed as $\chi_{r}^2$. \\
See Davidson and Mackinnon, Section 4.3.
* For a projection matrix, rank is equal to trace.

References:
* [StackExchange answer](https://stats.stackexchange.com/a/20230/261782) by ocram.
* Strang. *Introduction to Linear Algebra*. Section 6.4.
* Davidson and Mackinnon. *Econometric Theory and Methods*. Section 4.3.

### (3.11) $\hat{\beta}$ and $\hat{\sigma}^2$ are independent

### (3.12) Hypothesis testing of one parameter coefficient

$z_j \sim t_{N-p-1}$ if $z_j$ can be expressed as $\frac{a}{\sqrt{b / (N-p-1)}}$ where a and b are independent, $a \sim N(0,1)$, and $b \sim \chi_{N-p-1}^2$.

Note $\frac{\hat{\beta_j}}{\sigma \sqrt{v_j}} \sim N(0,1)$ because $\hat{\beta_j} \sim N(0, \sigma^2 v_j)$ from (3.10). Also, $(N-p-1)\hat{\sigma^2} / \sigma^2 \sim \chi_{N-p-1}^2$ from (3.11).

Therefore, $z_j = \frac{\hat{\beta_j}}{\hat{\sigma}\sqrt{v_j}} = \frac{\hat{\beta_j} / \sigma \sqrt{v_j}}{\hat{\sigma} / \sigma} \sim t_{N-p-1}$. 

Alternatively, Section 4.4 in Davidson and Mackinnon derives:

1. The $z_j$ in (3.12) by using [FWL theorem](https://en.wikipedia.org/wiki/Frisch%E2%80%93Waugh%E2%80%93Lovell_theorem) to extract the estimate and variance of a subset of coefficients in $\hat{\beta}$.
1. If we know the true $\sigma$, then $z_j \sim N(0,1)$ under $\beta_j = 0$, 
1. If we estimate $\sigma$ using $\hat{\sigma}$, then $z_j \sim t_{N-p-1}$ under $\beta_j = 0$.

References:
* Davidson and Mackinnon. *Econometric Theory and Methods*.

### (3.13) Hypothesis testing of a group of parameters

Also see Section 4.4 in Davidson and Mackinnon.

### (3.13) F statistic for a single coefficient is equivalent to square of the Z-score

See [Exercise 3.1](/esl/03_02_Exercises)

### (3.19) Gauss-Markov Theorem

See [Exercise 3.3 (a)](/esl/03_02_Exercises)

### (3.40) Multivariate weighted RSS arises from Gaussian theory

### (3.40) Multivariate weighted RSS has same solution as (3.39)

See [Exercise 3.11](/esl/03_02_Exercises)

### (3.40) If the $\Sigma_i$ vary among observations, errors no longer decouple



