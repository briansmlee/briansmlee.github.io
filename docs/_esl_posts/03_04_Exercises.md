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
&= \arg\max_{\beta} \log p(\beta \lvert y, X)\\
&= \arg\max_{\beta} \log p(y \lvert \beta, X) + \log p(\beta)\\
&= \arg\max_{\beta} \log \frac{\exp(- (y - X\beta)^T (y - X\beta) / 2\sigma^2)}{\sqrt{(2\pi)^N N \sigma^2}} + \log \frac{\exp(- \beta^T \beta / 2\gamma)}{\sqrt{(2\pi)^p p \gamma}}\\
&= \arg\max_{\beta} -\frac{1}{2\sigma^2} (y - X\beta)^T (y - X\beta) - \frac{1}{2\gamma} \beta^T\beta\\
&= \arg\max_{\beta} \frac{1}{\sigma^2} \beta^TX^Ty -\frac{1}{2\sigma^2} \beta^TX^TX\beta - \frac{1}{2\gamma} \beta^T\beta\\
\end{align*} $$

By taking derivative, we obtain

$$\nabla_{\beta} = \frac{1}{\sigma^2} X^Ty - \frac{1}{\sigma^2} X^TX\beta - \frac{1}{\gamma} \beta = 0$$

Hence, if $\gamma = \sigma^2 / \lambda$, the mode is equal to the ridge regression solution.

For the mean, note that the posterior is Gaussian because $p(\beta \lvert y, X) \propto p(y \lvert \beta, X) p(\beta)$ and both likelihood and prior are Gaussian (see Paisley Lecture 5 for a more formal explanation). For a Gaussian distribution, mean is equal to the mode.

References:
* Paisley. [*ColumbiaX - CSMM.102x: Machine Learning*](https://www.edx.org/course/machine-learning). Lecture 4 and 5.
* [StackExchange answer](https://math.stackexchange.com/a/2211829/455856) by tibL.

### 3.7

*Assume $y_i \sim N(\beta_0 + x_i^T \beta, \sigma^2)$ and $\forall j > 0, \beta_j \overset{\text{i.i.d}}{\sim} N(0, \gamma^2)$. Show that the log-posterior is proportional to $\sum_i [(y_i - \beta_0 - x_i^T \beta)^2] + \lambda \beta^T\beta$ from (3.41).*

Assuming that $y_i$ are conditionally independent:

$$ \begin{align*}
\log p(\beta \lvert y, X) &\propto \log p(y \lvert \beta, X) + \log p(\beta) \\
&\propto \log \prod_i [p(y_i \lvert \beta, x_i)] + \log p(\beta) \\
&\propto \sum_i [\log p(y_i \lvert \beta, x_i)] + \log p(\beta)\\
&= \sum_i [\log \frac{\exp(- (y_i - \beta_0 - x_i^T \beta)^2 / 2 \sigma^2)}{\sigma \sqrt{2 \pi}}] + \log \frac{\exp(- \beta^T \beta / 2\gamma^2)}{\sqrt{(2\pi)^p p \gamma^2}}\\
&\propto \sum_i [- \frac{1}{2\sigma^2} (y_i - \beta_0 - x_i^T \beta)^2] -\frac{1}{2\gamma^2} \beta^T \beta\\
&= -\frac{1}{2\sigma^2} \sum_i [(y_i - \beta_0 - x_i^T \beta)^2] + \lambda \beta^T \beta\\
\end{align*}$$

which is proportional to the given sum.

### 3.8

*Let $X$ be a of N x (p + 1) matrix with a first column of ones. Let $Q_2$ be the N x p matrix with first column removed from the QR decomposition of $X$. Let $\tilde{X}$ be the N x p centered matrix without the first column of $X$. Let $UDV^T$ be the SVD of $\tilde{X}$.*

*1. Show that $Q_2$ and $U$ span the same subspace.*

$U$ trivially spans $C(\tilde{X})$ because $DV^T$ gives the linear combinations. So, let's show that $Q_2$ also spans $C(\tilde{X})$, which is equivalent to linearly combining columns of $Q_2$ to obtain each $\tilde{x}\_j$.

$$ \begin{align*} 
\tilde{x}_j 
&= x_j - \overline{x}_j \mathbf{1}\\
&= x_j - (\frac{\mathbf{1}^T x_j}{N}) \mathbf{1}\\
&= x_j - (\frac{\sqrt{N} q_0^T x_j}{N}) \sqrt{N} q_0 && \text{since $q_0 = \mathbf{1} / \sqrt{N} $}\\
&= x_j - (q_0^T x_j) q_0\\
&= \sum_{k = 0}^{j} (q_k^T x_j) q_k - (q_0^T x_j) q_0 && \text{from Gram-Schmidt (see below)}\\
&= \sum_{k = 1}^{j} (q_k^T x_j) q_k
\end{align*} $$

which is a linear combination of the columns of $Q_2$.

From Gram-Schmidt and QR decomposition, $r_{jk} = x_j^Tq_k$. So $x_j = Qr_j = \sum_{k = 0}^{j} (q_k^T x_j) q_k$, a linear combination of ($x_j$'s projection onto) $q_k$s from $k=0$ to $j$ (see Strang Section 4.4).

By subtracting $\overline{x}\_j \mathbf{1}$ or $(q_0^T x_j) q_0$ from $x_j$, we have removed the $q_0$'s contribution to that linear combination. Hence, $\tilde{x}\_j$ can be linearly combined without the first column of $Q$ thereby only using the columns of $Q_2$.

### 3.12

*Augment $X$ with $\sqrt{\lambda}I\_{p}$ and $y$ with $\mathbf{0}\_{p}$ additional rows. Show that OLS estimate on the augmented data yields ridge regression estimates for $X$ and $y$.*

Follows from $X_{new}^T X_{new} = X^T X + \lambda I_p$ and $X_{new}^T y_{new} = X^T y$ using block multiplication (see Strang Section 2.4).

### 3.16

*If columns of $X$ are orthonormal find j-th coefficient estimate.*

*1. Subset Selection estimate is $\hat{\beta}\_j \cdot I[\lvert \hat{\beta_j} \rvert  \geq \lvert \hat{\beta}\_{(M)} \rvert]$*

$$ \begin{align*}
RSS_{subset} 
&= \lVert y - X_{subset}\hat{\beta}_{subset} \rVert^2 \\
&= \lVert y - X\hat{\beta} + \sum_{j \in D} \hat{\beta}_j x_j \rVert^2 && \text{let D be the set of dropped coefficients' indices} \\
&= \lVert y - X\hat{\beta} \rVert^2 + \lVert \sum_{j \in D} \hat{\beta}_j^2 x_j \rVert^2 && \text{residual and linear combination of $x_j$s are orthogonal}\\
&= \lVert y - X\hat{\beta} \rVert^2 + \sum_{j \in D} \hat{\beta}_j^2 \lVert x_j \rVert^2 && \text{$x_j$s are mutually orthogonal}\\
&= RSS + \sum_{j \in D} \hat{\beta}_j^2 && \text{$x_j$ are normal}\\
\end{align*} $$

Hence to minimize $RSS\_{subset}$, subset selection drops coefficients with smallest $\lvert \hat{\beta}\_j \rvert$ or keeps coefficients $\lvert \hat{\beta_j} \rvert  \geq \lvert \hat{\beta}\_{(M)} \rvert$.

*2. Ridge estimate is $\hat{\beta}\_j / (1 + \lambda)$*

Because $(X^TX + \lambda I)^{-1}X^Ty = (I + \lambda I)^{-1}X^Ty = X^Ty / (1 + \lambda)$ and OLS estimate is $X^Ty$.

*3. Lasso estimate is $sign(\hat{\beta}_{j})(\lvert \hat{\beta}_{j} \rvert - \lambda)\_{+}$*

See [this StackExchange answer](https://stats.stackexchange.com/a/17786/261782) by user cardinal.

### 3.17

### 3.23

### 3.24

### 3.25

### 3.26

### 3.27

### 3.28

### 3.29

### 3.30