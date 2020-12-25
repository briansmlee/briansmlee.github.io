---
layout: page
title: 4.5 Separating Hyperplanes - Exercises
permalink: /esl/04_05_Exercises/
chapter_title: 4 Linear Methods for Classification
section_title: 4.5 Separating Hyperplanes
type: Exercises
usemathjax: true
---

* toc
{:toc}

### 4.6

### 4.7

*Consider $D^\ast(\beta, \beta_0) = - \sum_{i=1}^N y_i (x_i^T \beta + \beta_0)$, a generalization of the Perceptron criterion. Is minimizing $D^\ast$ subject to $\lVert \beta \rVert = 1$ equivalent to solving the optimal separating hyperplane problem?*

$D^\ast = - \sum_{i \in M} y_i (x_i^T \beta + \beta_0) - \sum_{i \in M^c} y_i (x_i^T \beta + \beta_0)$ is the sum of distances of misclassified points to the decision boundary minus that of correctly-classified points. If data is linearly separable, all points can be correctly classified, so minimizing $D^\ast$ is maximizing the sum of distances of all the points to the decision boundary.

This is not equivalent to the optimal separating hyperplane problem, where *each* point needs to be at least a distance away from the decision boundary and  $\beta$ is defined only in terms of the support points.

TODO: Link to the LDA solution, which depends on all the data.