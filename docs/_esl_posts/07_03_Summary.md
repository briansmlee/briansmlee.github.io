---
layout: page
title: 7.3 The Bias-Variance Decomposition - Summary
permalink: /esl/07_03_Summary/
chapter_title: 7 Model Assessment and Selection
section_title: 7.3 The Bias-Variance Decomposition
type: Summary
usemathjax: true
---

Assume $Y = f(X) + \varepsilon$, $E[\varepsilon] = 0, Var[\varepsilon] = \sigma^2$. EPE of regression model $\hat{f}$ at $X = x_0$ using squared-error loss is:

$$Err(x_0) = \sigma^2 + (\underbrace{f(x_0) - E[\hat{f}(x_0)]}_{\text{Bias}})^2 + \underbrace{E[(\hat{f}(x_0) - E[\hat{f}(x_0)])^2]}_{\text{Variance}}$$

As complexity $\uparrow$, variance $\uparrow$ and bias $\downarrow$. We can derive bias and variance terms for k-nearest neighbor and linear models. 
- kNN: as $k \downarrow$, complexity $\uparrow$.
- linear model: as $p \uparrow$, complexity $\uparrow$.

For the linear model family, the bias decomposes further: 

$$E_{x_0}[\text{Bias}^2] = E_{x_0}[\underbrace{(f(x_0) - x^T_0 \beta_{\ast})^2}_{\text{Model bias}}] + E_{x_0}[\underbrace{(x^T_0 \beta_{\ast} - E[x^T_0 \hat{\beta}_\alpha])^2}_{\text{Estimation bias}}]$$

- Model bias: can only be reduced by enlarging the class of models (basis expansions). 
- Estimation bias: is zero for OLS. Restricted fits (ridge, Lasso) tradeoff positive estimation bias with lower variance.

### 7.3.1 Example

For classification (0-1) loss, prediction error might not be sum of squared bias and variance; even though bias rises, prediction error can decrease or stay the same. TODO: "Estimation errors that leave us on right side of decision boundary doesn't hurt."

Bias-variance tradeoff behaves differently for squared and 0-1 loss, so best tuning parameters differ.