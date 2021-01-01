---
layout: page
title: 7.6 Effective Number of Parameters - Summary
permalink: /esl/07_06_Summary/
chapter_title: 7 Model Assessment and Selection
section_title: 7.6 Effective Number of Parameters
type: Summary
usemathjax: true
---

How do we generalize "the number of parameters", for regularized or non-linear models?

For a linear fitting method $\hat{y} = Sy$, **effective degrees of freedom** is defined as $\text{df}(S) = \text{tr}(S)$. If S is orthogonal projection matrix, $\text{tr}(S) = d$.

Also, define $\text{df}(\hat{y}) = \frac{\sum_i Cov(\hat{y_i}, y_i)}{\sigma^2_\varepsilon}$. If additive-error model, this equals $\text{tr}(S)$.

TODO: df for neural networks.