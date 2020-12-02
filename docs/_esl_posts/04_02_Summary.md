---
layout: page
title: 4.2 Linear Regression of an Indicator Matrix - Summary
permalink: /esl/04_02_Summary/
chapter_title: 4 Linear Methods for Classification
section_title: 4.2 Linear Regression of an Indicator Matrix
type: Summary
usemathjax: true
---

Fit $k$ linear regression models as discriminant functions using indicator response matrix.

Interpret each regression as an estimate of conditional expectation $E(Y_k \lvert X = x)$, which is equal to $P(G = k \lvert X = x)$. 

Is linear regression a good estimate of the posterior? Estimates sum to 1, but can be negative or greater than 1.

Masking problem with $K \geq 3$: even though classes are separable, the model masks a class because its fitted regression value is never dominant. Occurs when $K$ is large but $p$ is small.