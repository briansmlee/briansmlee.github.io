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

### (3.4) Differentiate RSS w.r.t. $\beta$

Differentiate RSS($\beta$) $ = y^T y - 2 \beta^T X^T y + \beta^T X^TX \beta$. Note $\frac{\partial}{\partial \beta} \beta^T X^T y = X^Ty$. Show $ \frac{\partial}{\partial \beta} \beta^T X^T X \beta = 2 X^T X\beta$. 

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

From the two partial derivatives, we obtain $ \frac{\partial}{\partial \beta} RSS = - 2 X^T (y - X \beta)$, which we set to zeros for the normal equation.

Reference:
* Barnes. [*Matrix Calculus*](https://atmos.washington.edu/~dennis/MatrixCalculus.pdf). Section 5.


### (3.8) Covariance matrix of OLS estimate
![Derive (3.8)](/assets/esl/3.8.jpg)

Reference: [EdX ColumbiaX Machine Learning](https://www.edx.org/course/machine-learning), Lecture 3.

### (3.8) Estimate $\hat{\sigma}^2$ of $y_i$'s variance $\sigma^2$ is unbiased

See [this Math StackExchange answer](https://math.stackexchange.com/a/2342977/455856). Note that this answer assumes that the variance $\sigma^2$ of $y_i$ comes from $\varepsilon \sim N(0, \sigma^2)$.

TODO: Is it possible to derive without the assumption above?

### (3.10) Under (3.9), OLS estimate is normal

![Derive (3.10)](/assets/esl/3.10.jpg)

### (3.11) $\hat{\sigma}^2$ has chi-squared distribution with $N-p-1$

See [this Math StackExchange answer](https://stats.stackexchange.com/a/20230/261782). Below slightly extends the answer by using (imo) a bit easier linear algebra.

![Derive (3.11)](/assets/esl/3.11.jpg)

### (3.11) $\hat{\beta}$ and $\hat{\sigma}^2$ are independent

### (3.12) Hypothesis testing of one parameter coefficient

The "Z-score" in (3.12) is a [T-statistic](https://en.wikipedia.org/wiki/T-statistic), because we don't know the population mean nor standard deviation; we are estimating from a sample.

TODO: Derive that T-statistic takes T-distribution.

Chapter 4 from *Econometric Theory and Methods* by Davidson and Mackinnon provides a self-contained explanation of hypothesis testing in linear regression models. Specifically, see section 4.4.

### (3.19) Gauss-Markov Theorem

See [Exercise 3.3 (a)](/esl/03_02_Exercises)

### (3.40) Multivariate weighted RSS arises from Gaussian theory

### (3.40) Multivariate weighted RSS has same solution as (3.39)

See [Exercise 3.11](/esl/03_02_Exercises)

### If the $\Sigma_i$ vary among observations, errors no longer decouple



