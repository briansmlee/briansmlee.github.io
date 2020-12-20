---
layout: page
title: 4.4 Logistic Regression - Exercises
permalink: /esl/04_04_Exercises/
chapter_title: 4 Linear Methods for Classification
section_title: 4.4 Logistic Regression
type: Exercises
usemathjax: true
---

* toc
{:toc}

### 4.4
See Weatherwax solution and Bishop Section 4.3.4.

With multi-class logistic regression, the log-likelihood of one sample is:

$$ \begin{align*}
\log P(G = g \lvert x; \theta) 
&= \log \prod_{l=1}^K P(G = l \lvert x; \theta)^{I[g_i = l]} \\ 
&= (\sum_{l=1}^{K-1} I[g_i = l] \log p_l) + I[g_i = K] \log p_K \\
&= \sum_{l=1}^{K-1} I[g_i = l] \beta_l^T x 
- \sum_{l=1}^{K-1} I[g_i = l] \log p_K^{-1}
+ I[g_i = K] \cdot - \log p_K^{-1} \\
&= \sum_{l=1}^{K-1} y_l \beta_l^T x - \sum_{l=1}^{K} I[g_i = l] \log p_K^{-1} \\
&= \sum_{l=1}^{K-1} y_l \beta_l^T x - \log p_K^{-1} \\
&= \sum_{l=1}^{K-1} y_l \beta_l^T x - \log (1 + \sum_{m=1}^{K-1} e^{\beta_m^Tx}) \\
\end{align*} $$

where $p_l = P(G = l \lvert x; \theta)$ and $y$ is a 0/1 encoded vector of length $K-1$. So, the log-likelihood of all samples is

$$L(\theta) = \sum_{i=1}^N \sum_{l=1}^{K-1} y_{il} \beta_l^T x_i - \log (1 + \sum_{m=1}^{K-1} e^{\beta_m^Tx_i})$$

For Newton-Raphson, we find the gradient and hessian of $L$ w.r.t. $\theta$, the $K - 1$ $\beta$s.

The gradient is a $K - 1$ by $p + 1$ matrix, where the first row is

$$ 
\frac{\partial L}{\partial \beta_1} 
= \sum_{i=1}^N y_{i1} x_i - \frac{1}{1 + \sum_{m=1}^{K-1} e^{\beta_m^Tx_i}} \cdot e^{\beta_1^Tx_i} \cdot x_i
= \sum_{i=1}^N (y_{i1} - p_{i1}) x_i
$$

### 4.5
