---
layout: page
title: 3.5 Methods using Derived Input Directions - Summary
permalink: /esl/03_05_Summary/
chapter_title: 3 Linear Methods for Regression
section_title: 3.5 Methods using Derived Input Directions
type: Summary
usemathjax: true
---

* toc
{:toc}

Given many highly correlated features, use few linear combinations of them.

### 3.5.1 Principal Components Regression

Use $M \leq p$ principal components. 

1. Since principal components are orthogonal, $\hat{y}$ is sum of univariate regressions.
2. Normalize features: principal components depend on scale of features.
3. Similar to ridge: instead of shrinking coefficients with smaller singular values, drop them.

### 3.5.2 Partial Least Squares

Each derived feature $z$ is a sum of inputs (orthogonalized w.r.t. prev feature), weighted by strength of univariate effect on $y$. At each step:
1. $z = \sum_i^p proj(y \rightarrow x_i)$
2. $\hat{y} \mathrel{+}= proj(y \rightarrow z)$
3. $x_i \mathrel{-}= proj(x_i \rightarrow z)$

Optimization formulation: PLS seeks directions that has high variance and are highly correlated with response.
