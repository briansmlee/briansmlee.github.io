---
layout: page
title: 7.6 Effective Number of Parameters - Exercises
permalink: /esl/07_06_Exercises/
chapter_title: 7 Model Assessment and Selection
section_title: 7.6 Effective Number of Parameters
type: Exercises
usemathjax: true
---

* toc
{:toc}

$\require{cancel}$

### 7.5

Analogous to Exercise 7.1. 

$$\sum_{i=1}^N Cov(\hat{y_i}, y_i) = tr[Cov(\hat{y}, y)] = tr[E[(\hat{y} - E[\hat{y}])(y - E[y])^T]] = tr[S \cancelto{Var(y)}{E[(y - E[y])(y - E[y])^T]}] = tr[S] \sigma^2$$

### 7.6

The kNN fit is

$$ \hat{y_i} = \frac{1}{k} \sum_{\{l : x_l \in N_i\}} y_l = \frac{1}{k} s_i^T y$$

where $N_i$ is the neighborhood of $k$ predictors closest to $x_i$. On the right, we have expressed the sum using a 0-1 vector $s_i$ of $K$ ones. Notice that i-th term in $s_i$ must be a one, because $x_i \in N_i$. Hence, kNN is a linear fitting method

$$ \hat{y} = \frac{1}{k} S y $$

where $s_i$ is i-th row of $S$, so diagonal entries of $S$ are ones. Consequently, $\text{df}(\hat{y}) = \text{tr}[\frac{1}{k}S] = \frac{N}{k}$.

