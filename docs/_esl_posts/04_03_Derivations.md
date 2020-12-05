---
layout: page
title: 4.3 Linear Discriminant Analysis - Derivations
permalink: /esl/04_03_Derivations/
chapter_title: 4 Linear Methods for Classification
section_title: 4.3 Linear Discriminant Analysis
type: Derivations
usemathjax: true
---

* toc
{:toc}

### (p113) LDA by data sphering and nearest centroid classification

See [Spring '13 CMU Data Mining: Lecture 21](https://www.stat.cmu.edu/~ryantibs/datamining/lectures/21-clas2.pdf) by Ryan Tibshirani, slides 4 and 5.

With sphered $x$ and $\mu_k$, the LDA discriminant function becomes distance to the mean (plus log prior):

$$ \begin{align*}
\hat{\delta_1}(x) &= -\frac{1}{2} (x - \hat{\mu_1})^T \Sigma^{-1} (x - \hat{\mu_1}) + \log \hat{\pi_1}\\
&= -\frac{1}{2} (x - \hat{\mu_1})^T UD^{-1}U^T (x - \hat{\mu_1}) + \log \hat{\pi_1} \\
&= -\frac{1}{2} \lVert D^{-\frac{1}{2}} U^T (x - \hat{\mu_1}) \rVert^2 + \log \hat{\pi_1}\\
&= -\frac{1}{2} \lVert x^* - \mu_1^* \rVert^2 + \log \hat{\pi_1}\\
\end{align*} $$

Hence, to maximize the discriminant function, we minimize the distance to the centroid, modulo the log prior.
