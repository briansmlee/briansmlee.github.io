---
layout: page
title: 7.2 Bias, Variance, and Model Complexity - Summary
permalink: /esl/07_02_Summary/
chapter_title: 7 Model Assessment and Selection
section_title: 7.2 Bias, Variance, and Model Complexity
type: Summary
usemathjax: true
---

**Generalization performance** relates to prediction capability on independent test data. How do we assess generalization performance and use it to select models?

See Section 7.4 Summary for definitions of test error, expected test error, and training error.

We estimate (expected) test error for two reasons:
- **Model selection**: As complexity $\uparrow$, variance $\uparrow$ and bias $\downarrow$ Select complexity-tuning parameters $\alpha$ that minimizes EPE.
- **Model assessment**: Estimate test error for the selected model.

Use validation set for model selection and test set only for assessment.

Approximate the selection step analytically (AIC, BIC, MDL) or by efficient sample re-use (cross-validation, bootstrap).
