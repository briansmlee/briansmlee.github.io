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

*Show that the perceptron algorithm converges in finite number of steps.* 

(a) Suppose $\beta_a$ are the coefficients of a separating hyperplane. Then, $y_i \beta^T_a x^\ast_i > 0, \forall i$ and therefore $y_i \beta^T_a z_i > 0, \forall i$.

Let $c = \min_i y_i \beta^T_a z_i$. So, $y_i \beta^T_a z_i \geq c, \forall i$. If we set $\beta_{sep} = \beta_a / c$, we obtain $y_i \beta^T_{sep} z_i \geq 1, \forall i$.

(b) 

$$ 
\lVert \beta_{new} - \beta_{sep} \rVert^2 
= \lVert (\beta_{old} - \beta_{sep}) + y_i z_i \rVert^2
= \lVert \beta_{old} - \beta_{sep} \rVert^2 + 2 y_i z_i^T \beta_{old} - 2 y_i z_i^T \beta_{sep} + y^2_i z^T_i z_i
$$

Note:
- $y^2_i z^T_i z_i = 1$ because $y_i^2 = 1$ and $z^T_i z_i = {x^\ast_i}^T x^\ast_i / \lVert x^\ast_i \rVert^2 = 1$. 
- $$-2 y_i z^T_i \beta_{sep} \leq -2$$ from (a).
- $$2 y_i z_i^T \beta_{old} \leq 0$$ since decision boundary using $$\beta_{old}$$ misclassified $z_i$.

Hence, $$\lVert \beta_{new} - \beta_{sep} \rVert^2 \leq \lVert \beta_{old} - \beta_{sep} \rVert^2 -1$$. So, algorithm converges in no more than $$\lVert \beta_{start} - \beta_{sep} \rVert^2 $$ steps.

### 4.7

*Consider $D^\ast(\beta, \beta_0) = - \sum_{i=1}^N y_i (x_i^T \beta + \beta_0)$, a generalization of the perceptron criterion. Is minimizing $D^\ast$ subject to $\lVert \beta \rVert = 1$ equivalent to solving the optimal separating hyperplane problem?*

$D^\ast = - \sum_{i \in M} y_i (x_i^T \beta + \beta_0) - \sum_{i \in M^c} y_i (x_i^T \beta + \beta_0)$ is the sum of distances of misclassified points to the decision boundary minus that of correctly-classified points. If data is linearly separable, all points can be correctly classified, so minimizing $D^\ast$ is maximizing the sum of distances of all the points to the decision boundary.

This is not equivalent to the optimal separating hyperplane problem, where *each* point needs to be at least a distance away from the decision boundary and $\hat{\beta}$ is defined only in terms of the support points.

TODO: Link to the LDA solution, which depends on all the data.