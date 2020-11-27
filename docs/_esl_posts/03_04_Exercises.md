---
layout: page
title: 3.4 Shrinkage Methods - Exercises
permalink: /esl/03_04_Exercises/
chapter_title: 3 Linear Methods for Regression
section_title: 3.4 Shrinkage Methods
type: Exercises
usemathjax: true
---

* toc
{:toc}

### 3.5

See Weatherwax and Epstein's solution. Below only adds a bit of explanation:

*1. Show the correspondence between $\beta^c$ and $\beta$ and between $\beta^c_0$ and $\beta_0$.*

Rewrite the criteria (3.85) as $ \sum_i [y_i - (\beta^c_0 - \sum_j \overline{x}\_{j} \beta^c_j) - \sum_j x_{ij} \beta^c_j]^2 + \lambda \sum_j {\beta^c_j}^2 $.

Above is equivalent to the original ridge regression criteria (3.41) if $\beta_0 = \beta^c_0 - \sum_j \overline{x}\_{j} \beta^c_j$ and $\forall j > 0, \beta_j = \beta^c_j$.

*2. Characterize (solve) the solution for $\beta^c_0$ and $\beta^c$*

Since we've shown the correspondence between $\beta^c$ and $\beta$, let's solve (3.41) for $\beta_0$ then replace. In vector form:

$$
\hat{\beta_0} 
= \frac{d}{d\beta_0} \sum_i \beta_0^2 - 2 y_i \beta_0 + 2 x_i^T \beta \beta_0
= \sum_i 2\beta_0 - 2 y_i + 2 x_i^T \beta = 0
$$

where we ignored the irrelevant terms in the first equality. Since $\beta_0 = \beta^c_0 - \overline{x}^T \beta^c$ and $\beta = \beta^c$ we obtain:

$$ N \cdot \beta^c_0 = \sum_i y_i - \sum_i x_i^T \beta^c + N \cdot \overline{x}^T \beta^c$$

The later two terms cancel out by definition of sample mean, so $\beta^c_0 = \frac{\sum_i y_i}{N} = \overline{y}$.

For $\hat{\beta^c}$, since $\beta = \beta^c$ and the solution $(X^TX + \lambda I)^{-1}X^Ty$ does not involve $\beta_0$, we have the same solution for $\hat{\beta^c}$.

### 3.6

### 3.7

### 3.8

### 3.12

### 3.16

### 3.17

### 3.23

### 3.24

### 3.25

### 3.26

### 3.27

### 3.28

### 3.29

### 3.30