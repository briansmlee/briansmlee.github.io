---
layout: page
title: 7.3 The Bias-Variance Decomposition - Derivations
permalink: /esl/07_03_Derivations/
chapter_title: 7 Model Assessment and Selection
section_title: 7.3 The Bias-Variance Decomposition
type: Derivations
usemathjax: true
---

$\require{cancel}$

* toc
{:toc}

### (7.9) Bias-variance decomposition of expected prediction error (EPE) using squared loss

In (7.3), the EPE averages over the training set $\mathcal{T}$ and the test sample $X, Y$ from the population.

Since $X = x_0$ and $Y = f(x_0) + \varepsilon$, only the $\varepsilon$ and $\mathcal{T}$ are random. In other words, $f(x_0)$ is not random, but $\varepsilon$ and $\hat{f}(x_0)$ (which is a function of the training set $\mathcal{T}$) are random. Abbreviating $f(x_0)$ as $f$ and $\hat{f}(x_0)$ as $\hat{f}$, EPE becomes

$$ \begin{align*}
E[((f - \hat{f}) + \varepsilon)^2]
&= E[(f - \hat{f})^2 + 2 f \varepsilon - 2 \hat{f} \varepsilon + \varepsilon^2] \\
&= E[(f - \hat{f})^2] + 2 f \cancelto{0}{E[\varepsilon]} - 2 E[\hat{f} \varepsilon] + E[\varepsilon^2] \\
&= E[(f - \hat{f})^2] - 2 E[\hat{f}] \cancelto{0}{E[\varepsilon]} + (Var(\varepsilon) + \cancelto{0}{E[\varepsilon]^2}) \\
&= E[(f - \hat{f})^2] + \sigma^2_\varepsilon
\end{align*}$$ 

In the third line, $E[\hat{f} \varepsilon] = E[\hat{f}] E[\varepsilon]$ if we assume that $\varepsilon$ and $\mathcal{T}$ are (conditionally) independent. This is equal to

$$ \begin{align*}
\text{second line in (7.9)}
&= \sigma^2_\varepsilon + E[\hat{f}]^2 - 2E[\hat{f}]f + f^2 + E[\hat{f}^2 - 2 \hat{f} E[\hat{f}] + E[\hat{f}]^2] \\
&= \sigma^2_\varepsilon + \cancel{E[\hat{f}]^2} - 2E[\hat{f}]f + f^2 + E[\hat{f}^2] - \cancel{2 E[\hat{f}]^2} + \cancel{E[\hat{f}]^2} \\
&= \sigma^2_\varepsilon - 2E[\hat{f}]f + f^2 + E[\hat{f}^2] \\
\end{align*} $$

TODO: Show $\varepsilon$ and $\mathcal{T}$ are independent if $\varepsilon_i$ are i.i.d and $\varepsilon$ and training features $X$ are independent.

### (7.10) Bias-variance decomposition of K-nearest neighbors EPE

Note $$\hat{f}(x_0) = \frac{1}{k} \sum^k_{l=1} y_l = \frac{1}{k} \sum^k_{l=1} f(x_l) + \varepsilon_l$$. Then, $$E[\hat{f}(x_0)] = \frac{1}{k} \sum^k_{l=1} E[f(x_l)] + \cancelto{0}{E[\varepsilon_l]} = \frac{1}{k} \sum^k_{l=1} f(x_l)$$.

Bias term follows from definition. Assuming $\varepsilon$ are pairwise independent, variance is 

$$E[(\hat{f} - E[\hat{f}])^2] = E[(\frac{1}{k} \sum^k_{l=1} \varepsilon_l)^2] = \frac{1}{k^2} E[\sum^k_{l=1} \sum^k_{m=1} \varepsilon_l \varepsilon_m] = \frac{1}{k^2} \sum^k_{l=1} E[\varepsilon_l^2] = \frac{1}{k^2} k \cdot (Var(\varepsilon) - \cancelto{0}{E[\varepsilon_l]^2}) = \frac{\sigma^2_\varepsilon}{k} $$

### (7.11) Variance in linear regression EPE

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

### (7.12) Variance in linear regression in-sample EPE

$$\sum_i h(x_i)^T h(x_i) = \sum_i x^T_i (X^TX)^{-1} x_i = tr[X(X^TX)^{-1}X^T] = tr[I_p] = p$$

So, $$\frac{1}{N} \sum_i \lVert h(x_i) \rVert^2 \sigma^2_\varepsilon = \frac{p}{N} \sigma^2_\varepsilon$$.