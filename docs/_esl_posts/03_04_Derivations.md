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

