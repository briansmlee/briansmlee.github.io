---
layout: page
title: 3.2 Linear Regression Models and Least Squares - Summary
permalink: /esl/03_02_Summary/
chapter_title: 3 Linear Methods for Regression
section_title: 3.2 Linear Regression Models and Least Squares
type: Summary
usemathjax: true
---

* toc
{:toc}

### Linear regression model

Imagine a regression problem with feature vector $ X \in \mathbb{R}^{p+1} $ and response $ Y \in \mathbb{R} $.

The **linear regression model**:
1. Assumes that the **regression function** is a linear function of inputs: 
$E(Y \lvert X) = X^T \beta$.
1. Predicts output as a linear function of the parameters: $ \hat{Y} = X^T \hat{\beta}$.

### Least squares estimation method

We estimate the model parameter $\beta$ from training data: $X$ is $N$ x $(p + 1)$ and $y$ is $N$ x $1$. **Least squares (OLS) estimation method** finds the $\hat{\beta}$ that minimizes **residual sum of squares (RSS)**: $\lVert y - X\hat{\beta} \rVert^2$.

**OLS estimate** has a unique solution $\hat{\beta} = (X^T X)^{-1} X^T y$, if $X$ has full column rank. Else, we can drop redundant features.

Since $X^T (y - X\hat{\beta}) = 0$, residual vector is orthogonal to column space of $X$. Hence, $\hat{y} = X \hat{\beta} = Hy$ is orthogonal projection of $y$ onto column space of $X$. $H$ is **projection matrix**.

### Statistical properties of the OLS estimate

Assume following about true distribution of data:

1. Features $x_i$ are fixed, not random variables.
2. Responses $y_i$ are uncorrelated and have constant variance $\sigma^2$ : $Var(y) = \sigma^2 I$.

	Then, $Var(\hat{\beta}) = \sigma^2 (X^T X)^{-1}$. Additionally, assume:

3. Again, regression function is a linear function of inputs: $E(Y \lvert X) = X^T \beta$.
4. $ Y = E(Y \lvert X) + \varepsilon $, where $ \varepsilon \sim N(0, \sigma^2) $.

	Then, $ \hat{\beta} \sim N(\beta, \sigma^2 (X^T X)^{-1}) $. $\hat{\beta}$ is unbiased.

### Estimate variance of $y_i$

We further estimate $\sigma^2$ by $ \hat{\sigma}^2 = \frac{\lVert y - \hat{y} \rVert^2}{N - (p + 1)}$, so that $ \hat{\sigma}^2 $ is unbiased.

Then, $(N - p - 1) \hat{\sigma}^2 \sim \sigma^2 \chi^2_{N - p - 1}$.

### Hypothesis testing and confidence intervals with OLS estimate

### Gauss-Markov Theorem (3.2.2)

Given the assumptions 1 to 3 from above, the OLS estimate has the smallest variance (as well as the Mean Squared Error and Expected Prediction Error) among all linear unbiased estimates.

### From univariate to multiple regression (3.2.3)

If input features are orthogonal, each multiple linear regression OLS estimate $\hat{\beta}_i$ is equal to the univariate estimate of regressing $y$ on $x_i$. 


However, input features are usually not orthogonal, so we orthogonalize them by **Gram-Schmidt procedure**. Then, $\hat{\beta}_p$ is equal to the univariate estimate of regressing $y$ on $z_p$, the residual after regressing $x_p$ on all other features. Also, $Var(\hat{\beta}_p)$ = $ \sigma^2 / \lVert z_p \rVert^2 $, so $\hat{\beta}_p$ is unstable if $z_p$ is close to 0.


In matrix form, we obtain the **QR decomposition**, $ X = Z D^{-1} D \Gamma = QR$, where $Q$ is a N x (p+1) orthonormal matrix and $R$ is an upper triangular (invertible) matrix. Then, we obtain the entire OLS estimate $\hat{\beta} = R^{-1}Q^T y$ and $\hat{y} = QQ^T y$.

### Multiple outputs (3.2.4)

If errors are same across across each output's observations and are uncorrelated across the multiple outputs, multiple outputs do not affect each other's OLS estimates.

If the errors are correlated across the multiple outputs, use multivariate RSS criterion, which yields the same estimate. If the errors vary across observations, multiple outputs no longer decouple.
