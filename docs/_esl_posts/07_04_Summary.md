---
layout: page
title: 7.4 Optimism of the Training Error Rate - Summary
permalink: /esl/07_04_Summary/
chapter_title: 7 Model Assessment and Selection
section_title: 7.4 Optimism of the Training Error Rate
type: Summary
usemathjax: true
---

Definitions (terms *test*, *generalization*, and *prediction* are used interchangeably):
- **Test error (extra-sample error)**: $$Err_{\mathcal{T}} = E_{X^0,Y^0}[L(Y^0, \hat{f}(X^0)) \lvert \mathcal{T}]$$
- **Expected prediction error (EPE)**: $$Err = E_{\mathcal{T}}[Err_{\mathcal{T}}] = E_\mathcal{T} E_{X^0,Y^0}[L(Y^0, \hat{f}(X^0)) \lvert \mathcal{T}]$$
- **Training error**: $$\overline{err} = \frac{1}{N} \sum^N_{i=1} L(y_i, \hat{f}(x_i))$$
- **In-sample error**: $$Err_{in} = \frac{1}{N} \sum^N_{i=1} E_{Y^0}[L(Y^0_i, \hat{f}(x_i)) \lvert \mathcal{T}]$$ (observe new response $Y_i^0$ at each training input $x_i$)
- **Optimism**: $\text{op} = Err_{in} - \overline{err}$
- **Expected optimism**: $\omega = E_\mathbf{y}(\text{op})$ (predictors are fixed, expectation over training set outcomes $\mathbf{y}$)

$\overline{err}$ is not a good estimate of test error, since $\overline{err}$ drops to zero as we increase model complexity.

While our goal is to estimate $Err_{\mathcal{T}}$, we often estimate $Err$. Similarly, estimate $\omega$ rather than $\text{op}$.

For squared, 0-1, and other loss functions, $\omega = \frac{2}{N} \sum^N_{i=1} Cov(\hat{y_i}, y_i)$, "how strongly $y_i$ affects its own prediction". $\omega = \frac{2}{N} d \sigma^2_\varepsilon$ for linear fit $\hat{y_i}$ and approximately for other losses. Optimism $\uparrow$ as $d \uparrow$ and $N \downarrow$.

AIC and BIC proxy $Err$ using $E_y(Err_{in}) = E_y(\overline{err}) + \omega$. Cross-validation and bootstrap directly estimate the $Err$. Comparing relative in-sample errors are effective for model selection.


