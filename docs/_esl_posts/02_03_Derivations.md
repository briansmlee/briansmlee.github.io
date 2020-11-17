---
layout: page
title: 2.3 Least squares and Nearest Neighbors - Derivations
permalink: /esl/02_03_Derivations/
chapter: 02_03
chapter_title: 2.3 Least squares and Nearest Neighbors
type: Derivations
usemathjax: true
---

### Derive normal equations

Suppose $y$ is a N x 1 vector with N responses from training data, $X$ is N x d matrix with d features in each row, and $\beta$ is d x 1 parameters. 

Then RSS from (2.3) is equal to $(y - X \beta)^T(y - X \beta)$ because i-th entry in $ (y - X\beta) $ is equal to $(y_i - {x_i}^T \beta)$ in (2.3).

Then, $ RSS(\beta) = y^T y - y^T X \beta - (X \beta)^T y + (X \beta)^T (X \beta) = y^T y - 2 y^T X \beta + \beta^T X^TX \beta$

Differentiate each element w.r.t $ \beta $:

First, $ \frac{\partial}{\partial \beta} y^T X \beta = (y^T X)^T $. That is, $ \frac{\partial}{\partial \beta} a^T \beta $ is $a,$ because i-th entry is $ \frac{d}{d\beta_i} a^T \beta = a_i$.

Second, show $ \frac{\partial}{\partial \beta} \beta^T X^T X \beta = 2 (X^T X)\beta$. 

Let $ X^T X = A$. Then, $\beta^T A \beta = \sum_i^d \beta_i \sum_j^d A_{i,j} \beta_j$, because $ A_{i,:}\beta = \sum_j^d A_{i,j} \beta_j $. Reorder the sum to $\sum_i^d \sum_j^d A_{i,j} \beta_i \beta_j$.

Let's differentiate. k-th term of the partial derivative vector is $\frac{d}{d \beta_k} \sum_i^d \sum_j^d A_{i,j} \beta_i \beta_j$ 
= $\frac{d}{d \beta_k} [A_{k,k}{\beta_k}^2 + \sum_{i \neq k}^d A_{i, k} \beta_i \beta_k + \sum_{j \neq k}^d A_{k, j} \beta_k \beta_j].$ For visualization, consider a d x d matrix where each i,j-th entry has $A_{i,j} \beta_i \beta_j$. For each k, add up 2d - 1 entries in k-th row and column.

So, k-th entry in partial derivative is $2 A_{k,k} {\beta_k} + \sum_{i \neq k}^d A_{i, k} \beta_i + \sum_{j \neq k}^d A_{k, j} \beta_j = \sum_{i}^d A_{i, k} \beta_i + \sum_{j}^d A_{k, j} \beta_j$. Notice that $\sum_{j}^d A_{k, j} \beta_j$ is k-th entry of $A\beta$ and $\sum_{i}^d A_{i, k} \beta_i$ is k-th entry of $A^T \beta$.

Therefore, the partial derivative is $(A^T + A)\beta$, equivalent to $2 (X^T X)\beta$ since $X^T X$ is symmetric.

Using the two partial derivatives, we have

$ \frac{\partial}{\partial \beta} RSS = - 2 X^T y + 2 X^T X \beta$

By setting the derivative to a vector of zeros, we obtain the normal equation, $ X^T (y - X\beta) = 0$.

### Reference
- [Matrix Calculus by Randal J. Barnes](https://atmos.washington.edu/~dennis/MatrixCalculus.pdf), Section 5.
