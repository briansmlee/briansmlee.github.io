---
layout: page
title: 3.4 Shrinkage Methods - Derivations
permalink: /esl/03_04_Derivations/
chapter: 03_04
chapter_title: 3.4 Shrinkage Methods
type: Derivations
usemathjax: true
---

# (3.44) Ridge regression estimate

Follows from least squares derivations, because $\frac{\partial}{\partial \beta} \lambda \beta^T \beta = 2 \lambda \beta$.

# $X^T X + \lambda I$ is invertible

$X^T X$ is PSD, so its eigenvalues are non-negative. That is, $(u^T X^T) X u = \lVert Xu \lVert^2 \geq 0$ for any $u$, so for any eigenvalue $e$ and eigenvector $v$, $0 \leq v^T (X^T X v) = v^T e v = e \lVert v \lVert^2$, and therefore $e \geq 0$.

Adding $\lambda I$ shifts each eigenvalue of $X^T X$ by $\lambda$: $(X^T X + \lambda I)v = X^TXv + \lambda v = (e + \lambda)v$. So, eigenvalues of $X^T X + \lambda I$ are positive if $\lambda > 0$ (i.e. is positive definite).

Because all eigenvalues of $X^T X + \lambda I$ are positive, it is invertible. That is, by contradiction, if we assume $X^T X + \lambda I$ is singular, then $\exists x \neq 0$ s.t. $(X^T X + \lambda I)x = 0$, but then $0$ is an eigenvalue.

# (3.47) Analyze ridge regression estimate using SVD of $X$

$$ \begin{equation*} \begin{split}
X\hat{\beta}_{RR} &= X(X^TX + \lambda I)^{-1}X^Ty \\ 
&= UDV^T (VD^TU^T UDV^T + \lambda I)^{-1}VD^TU^Ty \\
&= UDV^T (VD^2 V^T + \lambda VV^T)^{-1}VD^TU^Ty \\
&= UDV^T (V (D^2 + \lambda I)V^T)^{-1}VD^TU^Ty \\
&= UDV^T V^{-T} (D^2 + \lambda I)^{-1} V^{-1} VD^TU^Ty \\
&= UD(D^2 + \lambda I)^{-1} DU^Ty
\end{split} \end{equation*} $$

$D(D^2 + \lambda I)^{-1} D$ is a diagonal matrix with $j$-th diagonal entry as $d_j^2 / (d_j^2 + \lambda)$. So, $j$-th column of $UD(D^2 + \lambda I)^{-1} D$ is $u_j \frac{d_j^2}{d_j^2 + \lambda}$. By right-multiplying $U^T$, we obtain (3.47), a sum of outer products.

Hence, features with smaller singular values $d_j$ are shrinked more.

# (3.49) Principal component $v_1$ of $X$ has $z_1 = Xv_1$ with max variance


