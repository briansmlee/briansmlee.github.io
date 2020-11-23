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

*F statistic for a single coefficient is equivalent to square of the Z-score.*

See Section 4.3 from Davidson and Mackinnon. Square of a R.V. that is distributed as $t_{N-p-1}$ is distributed as $F_{1, N-p-1}$:

F distribution is a ratio of two independent RVs with chi-squared distributions, $\frac{a_1 / n_1}{a_2 / n_2}$, where $a_1 \sim \chi_{n_1}^2$ and $a_2 \sim ~ \chi_{n_2}^2$.\\
t distribution is a ratio of standard normal and chi-squared RVs; $t = \frac{b}{(a / n)^{1/2}}$, where $b \sim N(0,1)$ and $a \sim \chi^2_{n}$.\\
Chi-squared distribution is a sum of squares of standard normals.

Then, $t^2 = \frac{b^2}{a / n} \sim F_{1, n}$ because $b^2 \sim \chi^2_{1}$.

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
&= \sigma^2 \lVert (I - H) c \rVert^2 && \text{i.e. $I - H$ is PSD}\\
&\geq 0
\end{split} \end{equation*} $$

Reference:
* Tulloch. [*Elements of Statistical Learning*](https://ajtulloch.github.io/PDFs/ESL-Solutions.pdf).

(b) *$\hat{\beta}$ is an unbiased estimate of $\beta$. Suppose $\widetilde{\beta}$ is another unbiased estimate. Show $Var(\widetilde{\beta}) - Var(\hat{\beta})$ is positive semidefinite.*

$Var(\widetilde{\beta}) - Var(\hat{\beta})$ is positive semidefinite iff $\forall b \neq 0, b^T (Var(\widetilde{\beta}) - Var(\hat{\beta})) b \geq 0$. This is equivalent to $Var(b^T \widetilde{\beta}) - Var(b^T \hat{\beta}) \geq 0$.

Later inequality is same as (a) if we can let $b^T \widetilde{\beta} = \widetilde{\theta} = c^T y$.
1. If $y \neq 0$, there exists a $c$ that can combine $y$ to obtain any $b^T \widetilde{\beta}$. So, the inequality follows from (a).
2. If $y = 0$, $Var(b^T \hat{\beta}) = 0$, so the inequality is trivially true.

### 3.4

*Obtain OLS coefficients from a single pass of Gram-Schmidt procedure. Express in terms of QR decomposition of X*

$X$ is decomposed into $Q$ and $R$ from a single run of Gram-Schmidt procedure; $X = (ZD^{-1})(D\Gamma) = QR$ (3.31). 

By QR decomposition, $\hat{\beta} = (R^T Q^TQR)^{-1}R^TQ^Ty = R^{-1}R^{-T}R^TQ^Ty = R^{-1}Q^Ty$ (3.32). 

Since $R \hat{\beta} = Q^T y$ and $R$ is upper triangular, we can solve for $\hat{\beta}$ by back-substitution, solving from p-th coefficient to first.

(It is a bit unclear if this exercise is asking for a modification of the step 2 in the Gram-Schmidt procedure such that the $\hat{\beta}$ can be obtained *without* the final back-substitution. However, since the computational complexity of Gram-Schmidt procedure $O(n^3)$ dominates that of back-substitution $O(n^2)$, the additional back-substitution is probably ok.)

Reference:
* Strang. *Introduction to Linear Algebra*. See chapters 2.6 and 11.1 for computational complexity of back-substitution (LU) and QR.

### 3.11

*Suppose a multiple-output linear regression problem where the errors are correlated between outputs. Show that solution to the weighted RSS criterion (3.40) is given by $(X^TX)^{-1}X^TY$, ignoring the correlations.*

Let $A = Y - XB$. Then, $\sum_{i=1}^N a_i^T \Sigma^{-1} a_i = tr[\Sigma^{-1} A^TA]$, where $a_i$ is the i-th row of $A$ as a column vector. This is because:

$$ \begin{equation*} \begin{split}
tr[\Sigma^{-1} A^TA] 
&= \sum_{j=1}^K \sum_{k=1}^K \Sigma^{-1}_{j,k} (A^TA)_{j,k}\\
&= \sum_{j=1}^K \sum_{k=1}^K \Sigma^{-1}_{j,k} \sum_{i=1}^N A^T_{j,i} A_{i,k}\\
&= \sum_{i=1}^N \sum_{j=1}^K \sum_{k=1}^K A_{i,j} \Sigma^{-1}_{j,k}  A_{i,k}\\
&= \sum_{i=1}^N a_i^T \Sigma^{-1} a_i\\
\end{split} \end{equation*} $$

So, RSS (3.40) is equivalent to $tr[\Sigma^{-1} (Y - XB)^T (Y - XB)]$. We find its derivative w.r.t. $B$:

$$ \begin{align*}
\frac{\partial}{\partial B} tr[\Sigma^{-1} (Y - XB)^T (Y - XB)]
&= \frac{\partial}{\partial B} - tr[\Sigma^{-1} B^TX^TY] - tr[\Sigma^{-1} Y^TXB] + tr[\Sigma^{-1}B^TX^TXB] \\
&= \frac{\partial}{\partial B} - 2 tr[B^TX^TY \Sigma^{-1}] - tr[B^TX^TXB \Sigma^{-1}]\\
&= -2X^TY\Sigma^{-1} + (X^TXB\Sigma^{-1} + (X^TX)^T B \Sigma^{-T})\\
&= -2X^TY\Sigma^{-1} + 2X^TXB\Sigma^{-1}\\
\end{align*} $$

where the trace derivatives are from Matrix Cookbook (103) and (117). By setting the derivative to zeros, we obtain $X^TXB\Sigma^{-1} = X^TY\Sigma^{-1}$, which yields (3.39) because $\Sigma^{-1}$ is invertible.

Reference:
* Weatherwax and Epstein. [*A Solution Manual and Notes for:
The Elements of Statistical Learning*](https://waxworksmath.com/Authors/G_M/Hastie/WriteUp/Weatherwax_Epstein_Hastie_Solution_Manual.pdf). See the solution for an easier explanation of the derivative.
* Petersen and Pedersen. [*Matrix Cookbook*](https://www.math.uwaterloo.ca/~hwolkowi/matrixcookbook.pdf).