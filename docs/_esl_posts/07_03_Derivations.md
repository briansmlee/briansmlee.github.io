---
layout: page
title: 7.3 The Bias-Variance Decomposition - Derivations
permalink: /esl/07_03_Derivations/
chapter_title: 7 Model Assessment and Selection
section_title: 7.3 The Bias-Variance Decomposition
type: Derivations
usemathjax: true
---

* toc
{:toc}

### (7.11) Variance in EPE of the linear regression model

$$
Var(\hat{f}) 
= E[(\hat{f} - E[\hat{f}])^2] 
= E[\hat{f}^2] - E[\hat{f}]^2
= E[h^Ty y^Th] - E[h^Ty]^2
$$

Since $y$ is random, above is equivalent to

$$
h^T E[yy^T] h - h^T E[y]E[y]^T h
= h^T (E[yy^T] - E[y]E[y]^T) h
= h^T Var(y) h
= \sigma^2_\varepsilon h^T h 
$$

where last equality assumes $Cov(y_i,y_j) = 0$.

### (7.12) Variance in in-sample EPE

$$\sum_i h(x_i)^T h(x_i) = \sum_i x^T_i (X^TX)^{-1} x_i = tr[X(X^TX)^{-1}X^T] = tr[I_p] = p$$

So, $$\frac{1}{N} \sum_i \lVert h(x_i) \rVert^2 \sigma^2_\varepsilon = \frac{p}{N} \sigma^2_\varepsilon$$.