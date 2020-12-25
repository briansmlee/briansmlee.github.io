---
layout: page
title: 4.5 Separating Hyperplanes - Derivations
permalink: /esl/04_05_Derivations/
chapter_title: 4 Linear Methods for Classification
section_title: 4.5 Separating Hyperplanes
type: Derivations
usemathjax: true
---

* toc
{:toc}

### (4.40) ${\beta^\ast}^T(x - x_0)$ is signed distance of $x$ to $L$

Pick $x_0$ as projection of $x$ onto $L$. Since $\beta^\ast$ and $x - x_0$ are parallel, ${\beta^\ast}^T(x - x_0) = \lVert \beta^\ast \rVert \lVert x - x_0 \rVert \cos\theta = \pm \lVert x - x_0 \rVert$.

### (4.52) Wolfe dual

$-\sum_i \alpha_i [y_i(x_i^T \beta + \beta_0) - 1] = -\sum_i \alpha_i y_i x_i^T \beta - \sum_i \alpha_i y_i \beta_0 + \sum_i \alpha_i$, which is $-\sum_i \alpha_i y_i x_i^T \beta + \sum_i \alpha_i$ from (4.51).

Adding $\frac{1}{2} \lVert \beta \rVert^2 = \frac{1}{2} (\sum_i \alpha_i y_i x_i)^T \beta$ from (4.50), we obtain $-\frac{1}{2} \sum_i \alpha_i y_i x_i^T \beta + \sum_i \alpha_i$. 

Substituting $\beta$ again, $-\frac{1}{2} (\sum_i \alpha_i y_i x_i)^T(\sum_k \alpha_k y_k x_k) + \sum_i \alpha_i = -\frac{1}{2} \sum_i \sum_k \alpha_i \alpha_k y_i y_k x_i^T x_k + \sum_i \alpha_i$.

### (4.52) Maximizing the Wolfe dual in positive orthant gives solution

### (4.53) Solution must satisfy KKT conditions
