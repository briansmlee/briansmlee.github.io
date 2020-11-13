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

Need input normalization:
1. Standardize features, because coefficients of smaller-scaled features will be penalized more.
2. Intercept $\beta_0$ is not included in penalty term. Estimate $\beta_0 = \overline{y}$ and estimate other coefficients with feature-centered inputs.

Estimate is $ \hat{\beta_{RR}} = (X^T X + \lambda I)^{-1} X^T y $, where $X^T X + \lambda I$ is invertible.