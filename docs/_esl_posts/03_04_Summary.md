---
layout: page
title: 3.4 Shrinkage Methods - Summary
permalink: /esl/03_04_Summary/
chapter: 03_04
chapter_title: 3.4 Shrinkage Methods
type: Summary
usemathjax: true
---

# Shrinkage Methods

Because subset selection is discrete, resulting model can have high variance. Shrinkage methods are more continuous.

# 3.4.1 Ridge Regression

Minimizes penalized  ($\lambda \beta^T \beta$) RSS. $\lambda$ is complexity parameter.

With OLS, coefficients of correlated features can have high variance; large positive coefficients offset effect of large negative coefficients.

Need feature normalization:
1. Standardize features: otherwise, coefficients of smaller-scaled features will be penalized more.
2. Center features: intercept $\beta_0$ is not included in penalty term. Estimate $\beta_0 = \overline{y}$ and estimate other coefficients with centered features.

Estimate is $ \hat{\beta_{RR}} = (X^T X + \lambda I)^{-1} X^T y $, where $X^T X + \lambda I$ is invertible if $\lambda > 0$.

Using SVD, $X \hat{\beta}\_{LS} = UU^Ty $ and $X\hat{\beta}\_{RR} = \sum_i^p u_i \frac{d_i^2}{d_i^2 + \lambda} u_i^T y$. p-th coordinate $u_p^T y$ of the basis $U$ is shrinked the most because it has smallest singular value $d_p$. 

Also, first principal component $z_1 = Xv_1$ has maximal variance among all directions in $C(X)$ and subsequent components (with smaller singular values) have smaller variance. Hence, ridge regression shrinks directions with smaller variance.

Effective degrees of freedom is $df(\lambda) = \sum_i^p \frac{d_i^2}{d_i^2 + \lambda}$.

# 3.4.2 Lasso

$L_1$ penalty $\sum_1^p \lVert \beta_j \rVert \leq t$.

Solution is nonlinear w.r.t. $y_i$, and there is no closed form solution. Use LAR (3.4.4) for minimizing Lasso penalty.

Continuous subset selection: sufficiently small $t$ will cause some coefficients to be zero. 

Standardized parameter is $ s = t / \sum_1^p \lVert \hat{\beta}^{LS}\_i \rVert$.


