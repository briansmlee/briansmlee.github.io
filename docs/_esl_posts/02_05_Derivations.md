---
layout: page
title: 2.5 Local Methods in High Dimensions - Derivations
permalink: /esl/02_05_Derivations/
chapter: 02_05
chapter_title: 2.5 Local Methods in High Dimensions
type: Derivations
usemathjax: true
---

Curse of dimensionality

# Cube example

Suppose a p-dimensional hypercube. The edge length $$e$$ of the hypercube that captures fraction $$r$$ of the volume is $$e = r^{1/p}$$ because $$r / 1 = e^p$$. 

For example, in 10-dimensions, edge length of 0.5 captures only 0.001 of the volume.

# Bias-variance decomposition of MSE

See (2.25). I will write the true value $$f(x_0)$$ as $$f$$ and prediction $$\hat{y}$$ as $$y$$. All expectations are across the training set $$T$$.

Variance is the expectation of squared deviation of a random variable from its expectation, $$E [(y - E[y])^2]$$. Bias is deviation of an estimator's expectation from the true value, $$E[y] - f$$.

Then, $$Var(y) + Bias(y)^2 = E [(y - E[y])^2] + (E[y] - f)^2$$, which we expand to $$E[y^2 - 2 y E[y] + E[y]^2] + (E[y]^2 - 2 E[y]f + f^2).$$

By lineararity of expecation, this is equivalent to $$E[y^2] - E[2 y E[y]] + E[E[y]^2] + E[y]^2 - 2 E[y]f + f^2 
= E[y^2] - 2 E[y]^2 + E[y]^2 + E[y]^2 - 2 E[y]f + f^2,$$ because the expectation $$E[y]$$ is not random (that is, $$E[E[y]] = E[y]$$). Terms cancel to $$E[y^2] - 2 E[y]f + f^2$$.

Mean Squared Error is $$E[(f - y)^2] = E[f^2 - 2fy + y^2] = f^2 - 2fE[y] + E[y^2]$$ because the true value $$f$$ is not random. Hence, we decomposed MSE into squared bias and variance.
