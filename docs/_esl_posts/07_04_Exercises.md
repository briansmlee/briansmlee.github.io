---
layout: page
title: 7.4 Optimism of the Training Error Rate - Exercises
permalink: /esl/07_04_Exercises/
chapter_title: 7 Model Assessment and Selection
section_title: 7.4 Optimism of the Training Error Rate
type: Exercises
usemathjax: true
---

* toc
{:toc}

$\require{cancel}$

### 7.1

Let $h_i = X(X^TX)^{-1}x_i$. Then $\hat{y_i} - E[\hat{y_i}] = h_i^T(y - E[y])$. Therefore

$$\sum_i Cov(\hat{y_i}, y_i) = \sum_i E[(\hat{y_i} - E[\hat{y_i}])(y_i - E[y_i])] = \sum_i h_i^T E[(y - E[y])(y_i - E[y_i])])$$

$E[y_i] = f(x_i) + E[\varepsilon_i] = f(x_i)$. So $y_i - E[y_i] = \varepsilon_i$ and $y - E[y]$ is a N-vector $\varepsilon$ of errors $\varepsilon_i$.

Then $E[(y - E[y])(y_i - E[y_i])] = E[\varepsilon \cdot \varepsilon_i]$, a N-vector where the i-th term is $E[\varepsilon_i^2] = \sigma^2$ and other (j-th) terms are $E[\varepsilon_i \varepsilon_j] = E[\varepsilon_i] E[\varepsilon_j] = 0$ since $i \neq j$ and errors are independent. Hence

$$\sum_i h_i^T E[(y - E[y])(y_i - E[y_i])]) = tr[X(X^TX)^{-1}X^T \sigma^2 I_N] = \sigma^2 tr[\cancelto{I_d}{X^TX(X^TX)^{-1}}] = d \sigma^2 $$ 

More succinctly, 

$$ \begin{align*}
\sum_{i=1}^N Cov(\hat{y_i}, y_i) 
&= tr[Cov(\hat{y}, y)] \\
&= tr[E[(\hat{y} - E[\hat{y}])(y - E[y])^T]] \\
&= tr[X(X^TX)^{-1}X^T \cancelto{Var(y) = \sigma^2 I_N}{(y - E[y])(y - E[y])^T}] \\
&= d \sigma^2
\end{align*} $$

### 7.4

See Weatherwax solution, contributed by Franklin Wang. I think the solution below uses same assumptions.

$\hat{f}(x_i)$ is $\hat{y_i}$. We can write the expected optimism as

$$ \omega = E_\mathbf{y}[Err_{in} - \overline{\text{err}}]
= \frac{1}{N} \sum^N_{i=1} E_\mathbf{y}[E_{Y^0}[(Y^0_i - \hat{y_i})^2] - (y_i - \hat{y_i})^2]$$

using linearity of expectation to move the sum outside of $E_\mathbf{y}$. We need to show that the above is equivalent to

$$ \frac{1}{N} \sum^N_{i=1} 2 Cov(\hat{y_i}, y_i) = \frac{1}{N} \sum^N_{i=1} 2 E_\mathbf{y}[(y_i - E_\mathbf{y}[y_i])(\hat{y_i} - E_\mathbf{y}[\hat{y_i}])]$$

assuming that $y_i = f(x_i) + \varepsilon_i$, where $E[\varepsilon_i] = 0$ and $Var[\varepsilon_i] = \sigma^2$. Also, assume $Y_i^0 = f(x_i) + \varepsilon_i^0$. Errors are i.i.d.

In essence, there are two random variables, the training responses $\mathbf{y}$ and the new observation $Y_i^0$ at $x_i$ from $Err_{in}$. Randomness comes from the errors $\varepsilon$. All the variables except $f(x_i)$ are random as they are a function of $\mathbf{y}$ or $Y_i^0$.

Let's show the equality of the i-th term:

$$ E_\mathbf{y}[E_{Y^0}[(Y^0_i - \hat{y_i})^2] - (y_i - \hat{y_i})^2] 
= 2 E_\mathbf{y}[(y_i - E_\mathbf{y}[y_i])(\hat{y_i} - E_\mathbf{y}[\hat{y_i}])]$$

For abbreviation, we will remove the i subscripts and write $f(x_i)$ as $f$.

First, note $E_{Y^0}[Y^0] = f + E[\varepsilon^0] = f$ and $E_{Y^0}[{Y^0}^2] = f^2 + 2 f E[\varepsilon^0] + E[{\varepsilon^0}^2] = f^2 + \sigma^2$. Then

$$ E_{Y^0}[(Y^0 - \hat{y})^2] = E[{Y^0}^2] - 2 E[Y^0]\hat{y} + \hat{y}^2 = f^2 + \sigma^2 - 2f \hat{y} + \hat{y}^2$$

So, LHS is 

$$E_\mathbf{y}[(f^2 + \sigma^2 - 2f \hat{y} + \cancel{\hat{y}^2}) - (y^2 - 2y \hat{y} + \cancel{\hat{y}^2})] = \cancel{f^2 + \sigma^2 - E[y^2]} + 2 E[(y - f)\hat{y}]$$

Adding $2 E[(y - f) E[\hat{y}]] = 2 E[(f + \varepsilon) - f] E[\hat{y}] = 0$, we obtain the RHS

$$ 2 E[(y - f)(\hat{y} - E[\hat{y}])] = 2 Cov(y, \hat{y})$$ 