---
layout: page
title: 7.2 Bias, Variance, and Model Complexity - Summary
permalink: /esl/07_02_Summary/
chapter_title: 7 Model Assessment and Selection
section_title: 7.2 Bias, Variance, and Model Complexity
type: Summary
usemathjax: true
---

* toc
{:toc}

**Generalization performance** relates to prediction capability on independent test data. How do we assess generalization performance and use it to select models?

- **Test/prediction/generalization error** is $$Err_{T} = E_{X,Y}[L(Y, \hat{f}(X)) \lvert T]$$. 
- **Expected test error (EPE)** is $$Err = E_{X,Y,T}[L(Y, \hat{f}(X))] = E_{T}[Err_{T}]$$. 
- **Training error** is $\overline{err} = \frac{1}{N} \sum_i L(y_i, \hat{f}(x_i))$.

While our goal is to estimate $Err_{T}$, we often estimate $Err$. $\overline{err}$ is not a good estimate of test error, since $\overline{err}$ drops to zero as we increase model complexity.

We estimate (expected) test error for two reasons:
- **Model selection**: As complexity $\uparrow$, variance $\uparrow$ but bias $\downarrow$ Select complexity-tuning parameters $\alpha$ that minimizes EPE.
- **Model assessment**: Estimate test error for the selected model.

Use validation set for model selection and test set only for assessment.

Approximate the selection step analytically (AIC, BIC, MDL) or by efficient sample re-use (cross-validation, bootstrap).
