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

The log-likelihood of multi-class logistic regression for one sample is:

$$ \begin{align*}
\log P(G = g \lvert x; \theta) 
&= \log \prod_{l=1}^K P(G = l \lvert x; \theta)^{I[g_i = l]} \\ 
&= (\sum_{l=1}^{K-1} I[g_i = l] \log p_l) + I[g_i = K] \log p_K \\
&= \sum_{l=1}^{K-1} I[g_i = l] \beta_l^T x 
- \sum_{l=1}^{K-1} I[g_i = l] \log p_K^{-1}
+ I[g_i = K] \cdot - \log p_K^{-1} \\
&= \sum_{l=1}^{K-1} y_l \beta_l^T x - \sum_{l=1}^{K} I[g_i = l] \log p_K^{-1} \\
&= \sum_{l=1}^{K-1} y_l \beta_l^T x - \log p_K^{-1} \\
&= \sum_{l=1}^{K-1} y_l \beta_l^T x - \log (1 + \sum_{j=1}^K e^{\beta_j^Tx}) \\
\end{align*} $$

where $p_l = P(G = l \lvert x; \theta)$. So, log-likelihood of all samples is

$$\sum_{i=1}^N \sum_{l=1}^{K-1} y_{il} \beta_l^T x_i - \log (1 + \sum_{j=1}^K e^{\beta_j^Tx_i})$$

### 4.5
