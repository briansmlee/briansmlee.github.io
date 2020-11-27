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

See Weatherwax and Epstein's solution; below only adds a bit of explanation. $\beta$ below excludes the intercept $\beta_0$.

*1. Show the correspondence between $\beta^c$ and $\beta$ and between $\beta^c_0$ and $\beta_0$.*

Rewrite the criteria (3.85) as $ \sum_i [y_i - (\beta^c_0 - \sum_j \overline{x}\_{j} \beta^c_j) - \sum_j x_{ij} \beta^c_j]^2 + \lambda \sum_j {\beta^c_j}^2 $.

Above is equivalent to the original ridge regression criteria (3.41) if $\beta_0 = \beta^c_0 - \sum_j \overline{x}\_{j} \beta^c_j$ and $\forall j > 0, \beta_j = \beta^c_j$.

*2. Characterize (solve for) $\hat{\beta^c_0}$ and $\hat{\beta^c}$*

Since we've shown the correspondence between $\beta^c$ and $\beta$, let's solve (3.41) for $\beta_0$ then replace. In vector form:

$$
\hat{\beta_0} 
= \frac{d}{d\beta_0} \sum_i \beta_0^2 - 2 y_i \beta_0 + 2 x_i^T \beta \beta_0
= \sum_i 2\beta_0 - 2 y_i + 2 x_i^T \beta = 0
$$

where we ignored the irrelevant terms in the first equality. Since $\beta_0 = \beta^c_0 - \overline{x}^T \beta^c$ and $\beta = \beta^c$ we obtain:

$$ N \cdot \hat{\beta^c_0} = \sum_i y_i - \sum_i x_i^T \beta^c + N \cdot \overline{x}^T \beta^c$$

The later two terms cancel out by definition of the sample mean, so $\hat{\beta^c_0} = \frac{\sum_i y_i}{N} = \overline{y}$.

For $\hat{\beta^c}$, since $\beta = \beta^c$ and the solution $(X^TX + \lambda I)^{-1}X^Ty$ does not involve $\beta_0$, we have the same solution.

A similar result holds for the lasso intercept because the penalty term was not involved in characterizing $\hat{\beta^c_0}$.

References:

* Weatherwax and Epstein. *A Solution Manual and Notes for:
The Elements of Statistical Learning*.

### 3.6

*Assume likelihood $y \lvert \beta, X \sim N(X\beta, \sigma^2 I)$ and prior $\beta \sim N(0, \gamma I)$. Show that the mode and mean of the posterior is equivalent to the ridge regression estimate. Show relationship between $\lambda$, $\gamma$ and $\sigma^2$.*

The mode maximizes the posterior (maximum a posteriori estimation):

$$ \begin{align*}
\hat{\beta}_{MAP} 
&= \arg\max_{\beta} p(\beta \lvert y, X)\\
&= \arg\max_{\beta} \log p(\beta \lvert y, X) && \text{log increases monotonically}\\
&= \arg\max_{\beta} \log p(y \lvert \beta, X) + \log p(\beta)\\
&= \arg\max_{\beta} \log \frac{\exp(- (y - X\beta)^T (y - X\beta) / 2\sigma^2)}{\sqrt{(2\pi)^N N \sigma^2}} + \log \frac{\exp(- \beta^T \beta / 2\gamma)}{\sqrt{(2\pi)^p p \gamma}}\\
&= \arg\max_{\beta} -\frac{1}{2\sigma^2} (y - X\beta)^T (y - X\beta) - \frac{1}{2\gamma} \beta^T\beta\\
&= \arg\max_{\beta} \frac{1}{\sigma^2} \beta^TX^Ty -\frac{1}{2\sigma^2} \beta^TX^TX\beta - \frac{1}{2\gamma} \beta^T\beta\\
\end{align*} $$

By taking derivative, we obtain

$$\nabla_{\beta} = \frac{1}{\sigma^2} X^Ty - \frac{1}{\sigma^2} X^TX\beta - \frac{1}{\gamma} \beta = 0$$

Hence, if $\gamma = \sigma^2 / \lambda$, the mode is equal to the ridge regression solution.

For the mean, note that the posterior is Gaussian because $p(\beta \lvert y, X) \propto p(y \lvert \beta, X) p(\beta)$ and both likelihood and prior are Gaussian; see Paisley Lecture 5 for a more formal explanation. For a Gaussian distribution, mean is equal to the mode.

References:
* Paisley. [*ColumbiaX - CSMM.102x: Machine Learning*](https://www.edx.org/course/machine-learning). Lecture 4 and 5.
* [StackExchange answer](https://math.stackexchange.com/a/2211829/455856) by tibL.

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