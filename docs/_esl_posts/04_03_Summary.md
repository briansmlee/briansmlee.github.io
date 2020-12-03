---
layout: page
title: 4.3 Linear Discriminant Analysis - Summary
permalink: /esl/04_03_Summary/
chapter_title: 4 Linear Methods for Classification
section_title: 4.3 Linear Discriminant Analysis
type: Summary
usemathjax: true
---

* toc
{:toc}

### LDA and QDA

Bayes classifier: $\hat{G}(x)= \arg\max_{k} P(G = k \lvert X = x) = \arg\max_{k} \frac{P(X = x \lvert G = k) P(G = k)}{\sum_{l=1}^K P(X = x \lvert G = l) P(G = l)}$. Both LDA and QDA model each class-conditional density as Gaussian.

LDA arises with common covariance.
- Pairwise decision boundary is linear (hyperplane) because log-ratio is linear.
- Linear discriminant functions yield same decision boundary.
- Estimate prior, mean, and common covariance.

LDA and linear regression:
- If two-class, LDA direction is proportional to the coefficient vector from linear regression with +1 and -1 responses.
- If multi-class, LDA avoids the masking problem unlike linear regression.

QDA arises with differing covariance. 
- Log-ratio, pairwise decision boundary, and discriminant functions are quadratic.
- Estimate covariance matrix for each class.
- TODO: LDA has $O(K \cdot p)$ parameters whereas QDA has $O(K \cdot p^2)$.

LDA and QDA may perform well due to bias-variance tradeoff; incur bias of linear decision boundary because we can estimate it with lower variance.

### 4.3.1 Regularized Discriminant Analysis

Let each covariance be a weighted mix of common and individual covariances. Choose weight via cross-validation.

### 4.3.2 Computations for LDA
