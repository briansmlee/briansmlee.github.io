---
layout: page
title: 3.3 Subset Selection - Summary
permalink: /esl/03_03_Summary/
chapter_title: 3 Linear Methods for Regression
section_title: 3.3 Subset Selection
type: Summary
usemathjax: true
---

* toc
{:toc}

### Subset selection

By retaining a subset of features, we can improve:
1. Prediction accuracy, by trading higher bias for lower variance.
2. Interpretability, by narrowing down features with strongest effects.

### 3.3.1 Best-subset selection

For each subset size $k$ from $0$ to $p$, finds subset that gives smallest RSS. 

1. Best subsets are not necessarily nested.
2. Produce sequence of models increasing in complexity: RSS of the best subset decreases as $k$ increases, so cannot use RSS to select $k$.
3. Computationally infeasible if $p > 40$.

### 3.3.2 Forward and backward stepwise selection

Sequentially add or remove a feature that minimizes the subsequent RSS to the active set.

1\. Forward: Begin with intercept. Add the feature that maximizes $\lvert q^Ty \rvert$ ([Exercise 3.9](/esl/03_03_Exercises)).

Greedy. Higher RSS than best-subset selection, but: 
1. Computationally feasible
2. Has lower variance (with higher bias) because more constrained search TODO: formalize

2\. Backward: Removes feature with smallest Z-score.

Unlike Forward, Backward cannot be used if $ N <= p $ because $X^TX$ in the Z-score is not invertible.

### 3.3.3 Forward-Stagewise regression

At each step, selects a feature that is most correlated with the current residual. To current coefficient of that feature, adds univariate linear regression coefficient of the residual onto that feature.