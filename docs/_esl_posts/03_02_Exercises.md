---
layout: page
title: 3.2 Linear Regression Models and Least Squares - Exercises
permalink: /esl/03_02_Exercises/
chapter_title: 3 Linear Methods for Regression
section_title: 3.2 Linear Regression Models and Least Squares
type: Exercises
usemathjax: true
---

* toc
{:toc}

### 3.1

### 3.2

### 3.3

(a) *Assume $X$ is fixed, $E(y) = X\beta$, and $Var(y) = \sigma^2 I$. Then $\hat{\theta} = a^T \hat{\beta} = a^T(X^TX)^{-1}X^Ty$ is an unbiased estimate; $E(\hat{\theta})=a^T\beta$ from (3.18). Suppose another linear estimator $\widetilde{\theta} = c^Ty$ is also unbiased. Show $Var(\widetilde{\theta}) \geq Var(\hat{\theta})$.*

First, $a^T = c^T X$ because $a^T \beta = E(\widetilde{\theta}) = E(c^T y) = c^T E(y) = c^T X \beta$. Then

$$ \begin{equation*} \begin{split}
Var(\widetilde{\theta}) - Var(\hat{\theta}) &= c^T Var(y) c - a^T Var(\hat{\beta})a\\ 
&= \sigma^2 c^Tc - \sigma^2 a^T (X^TX)^{-1}a && Var(\hat{\beta}) = \sigma^2(X^TX)^{-1} \text{ from (3.10)} \\
&= \sigma^2 (c^Tc - c^T X (X^TX)^{-1} X^T c) \\
&= \sigma^2 c^T (I - X(X^TX)^{-1}X^T)c \\
&= \sigma^2 c^T (I - H)c && \text{H is projection matrix (3.7)} \\
&= \sigma^2 c^T (I - H)^T(I - H)c && (I - H)^2 = (I - H) = (I - H)^T \\
&= \sigma^2 \lVert (I - H) c \rVert^2 \\
&\geq 0
\end{split} \end{equation*} $$

Reference:
* [Solution](https://tullo.ch/static/ESL-Solutions.pdf) by Andrew Tulloch

(b) *$\hat{\beta}$ is an unbiased estimate of $\beta$. Suppose $\widetilde{\beta}$ is another unbiased estimate. Show $Var(\widetilde{\beta}) - Var(\hat{\beta})$ is positive semidefinite.*

$Var(\widetilde{\beta}) - Var(\hat{\beta})$ is positive semidefinite iff $\forall b \neq 0, b^T (Var(\widetilde{\beta}) - Var(\hat{\beta})) b \geq 0$. This is equivalent to $Var(b^T \widetilde{\beta}) - Var(b^T \hat{\beta}) \geq 0$.

Later inequality is same as (a) if we can let $b^T \widetilde{\beta} = \widetilde{\theta} = c^T y$.
1. If $y \neq 0$, there exists a $c$ that can combine $y$ to obtain any $b^T \widetilde{\beta}$. So, the inequality follows from (a).
2. If $y = 0$, $Var(b^T \hat{\beta}) = 0$, so the inequality is trivially true.

### 3.4


### 3.11
