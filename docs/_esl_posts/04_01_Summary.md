---
layout: page
title: 4.1 Introduction - Summary
permalink: /esl/04_01_Summary/
chapter_title: 4 Linear Methods for Classification
section_title: 4.1 Introduction
type: Summary
usemathjax: true
---

**Decision boundary** divides the feature space into labeled regions. We focus on **linear decision boundaries**.

**Discriminant analysis** models **discriminant function $\delta_k(x)$** for each class, then classifies to $\hat{G}(x) = \arg\max_k \hat{\delta_k}(x)$. 
- Decision boundary is $\delta_1(x) = \delta_2(x)$. 
- Example: fit $k$ linear regression models to class indicator responses. Hyperplane decision boundaries.

Modeling the posterior $P(G \lvert X = x)$ is a form of discriminant analysis.

If monotone transformation of the discriminant function or posterior is linear, then decision boundary is linear.
- Binary example: logit and log-odds TODO: what are the discriminant function, transform, and boundary?
- LDA and logistic regression both yield linear log-odds or logits; difference is the way the linear function is fit to the training data.

Alternative to discriminant analysis is explicitly modeling a linear boundary; **separating hyperplane** if two-class.
- Perceptron
- Optimally separating hyperplane

Generalizations: with quadratic basis expansion, linear decision boundary in augmented space map down to quadratic decision boundary in the original space.
