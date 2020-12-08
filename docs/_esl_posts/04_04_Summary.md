---
layout: page
title: 4.4 Logistic Regression - Summary
permalink: /esl/04_04_Summary/
chapter_title: 4 Linear Methods for Classification
section_title: 4.4 Logistic Regression
type: Summary
usemathjax: true
---

* toc
{:toc}

Model specifies $K - 1$ linear log-odds/logits: $$ \frac{P(G = k \lvert X = x)}{P(G = K \lvert X = x)} = \beta_{k0} + \beta_k^T x, k = 1,..., K - 1$$. 

Then $$ P(G = k \lvert X = x) = \frac{\exp(\beta_{k0} + \beta_k^T x)}{1 + \sum_{l=1}^{K-1} \exp(\beta_{l0} + \beta_l^T x)} $$ and $$ P(G = K \lvert X = x) = \frac{1}{1 + \sum_{l=1}^{K-1} \exp(\beta_{l0} + \beta_l^T x)} $$, 
<br> so the posteriors are in $[0,1]$ and sum to 1.

### 4.4.1 Fitting Logistic Regression Models

Maximum (conditional) likelihood estimation: $$L(\theta) = \log P(g_1,...,g_N \lvert x_1,...,x_N; \theta) = \sum_i \log P(G = g_i \lvert X = x_i; \theta) $$

Binary case: with 0-1 responses, MLE gives **score equations**: $$ \frac{\partial l(\beta)}{\partial \beta} = \sum_i x_i (y_i - P(G = 1 \lvert X = x_i; \beta)) = 0$$

Score equations can be solved by Newton-Raphson or coordinate-descent algorithms.

TODO: Newton-Raphson algorithm

### 4.4.3 Quadratic Approximations and Inference

### 4.4.4 $L_1$ Regularized Logistic Regression

Add $L_1$ penalty to log-likelihood for variable selection and shrinkage. 

TODO: Optimization methods:
- Nonlinear programming of concave function
- Weighted Lasso using quadratic approximations from Newton algorithm
- Path algorithms (LAR)
- Coordinate descent is efficient

### 4.4.5 Logistic Regression or LDA?

Log-posterior odds for both models are linear. However, 
- Logistic regression fits $P(G \lvert X)$ by maximizing (multinomial) conditional likelihood 
- LDA fits $P(X, G = k) = P(X \lvert G = k) P(G = k)$ by maximizing full likelihood

Equivalently, LDA fits marginal mixture density $$P(X) = \sum_k \pi_k \phi(X; \mu_k, \Sigma)$$.



