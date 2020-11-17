---
layout: page
title: 3.3 Subset Selection - Summary
permalink: /esl/03_03_Summary/
chapter: 03_03
chapter_title: 3.3 Subset Selection
type: Summary
usemathjax: true
---

### Subset selection

By retaining a subset of features, we can improve:
1. Prediction accuracy, by trading higher bias for lower variance.
2. Interpretability, by narrowing down features with strongest effects.

### 3.3.1 Best-subset selection

For each subset size $k$ from $0$ to $p$, finds subset that gives smallest RSS. 

1. Best subsets are not neccesarily nested.
2. Produce sequence of models increasing in complexity: RSS of the best subset decreases as $k$ increases, so cannot use RSS to select $k$.
3. Computationally infeasible if $p > 40$.

### 3.3.2 Forward and backward stepwise selection

Forward: Begin with intercept. Sequentially add a feature that decreases RSS the most.

Greedy. Higher RSS than best-subest selection, but: 
1. Computationally feasible
2. Has lower variance (with higher bias) because more constrained search TODO: formalize

Backward: Sequentially removes feature with smallest Z-score.

Unlike Forward, Backward cannot be used if $ N <= p $. TODO: why? Z-score calculation?

### 3.3.3 Forward-Stagewise regression

TODO