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

Minimize penalized  ($\lambda \beta^T \beta$) RSS. $\lambda$ is complexity parameter.

With OLS, coefficients of correlated features can have high variance; large positive coefficients offset effect of large negative coefficients.

Need feature normalization:
1. Standardize features: otherwise, coefficients of smaller-scaled features will be penalized more.
2. Center features: intercept $\beta_0$ is not included in penalty term. Estimate $\beta_0 = \overline{y}$ and estimate other coefficients with centered features.

Estimate is $ \hat{\beta_{RR}} = (X^T X + \lambda I)^{-1} X^T y $, where $X^T X + \lambda I$ is invertible if $\lambda > 0$.

Using SVD, $X \hat{\beta}\_{LS} = UU^Ty $ and $X\hat{\beta}\_{RR} = \sum_i^p u_i \frac{d_i^2}{d_i^2 + \lambda} u_i^T y$. p-th coordinate $u_p^T y$ of the basis $U$ is shrinked the most because it has smallest singular value $d_p$. 



