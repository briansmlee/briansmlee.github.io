---
layout: page
title: 3.2 Linear Regression Models and Least Squares - Derivations
permalink: /esl/3_2_derivations/
usemathjax: true
---

# (3.8) Covariance matrix of OLS estimate
![Derive (3.8)](/assets/esl/3.8.jpg)

Reference: [EdX ColumbiaX Machine Learning](https://www.edx.org/course/machine-learning), Lecture 3.

# (3.8) Estimate $$\hat{\sigma}^2$$ of $$y_i$$'s variance $$\sigma^2$$ is unbiased

See [this Math StackExchange answer](https://math.stackexchange.com/a/2342977/455856). Note that this answer assumes that the variance $$\sigma^2$$ of $$y_i$$ comes from $$\varepsilon \sim N(0, \sigma^2)$$.

TODO: Is it possible to derive without the assumption above?

# (3.10) Under (3.9), OLS estimate is normal

![Derive (3.10)](/assets/esl/3.10.jpg)

# (3.11) $$\hat{\sigma}^2$$ has chi-squared distribution with $$N-p-1$$

See [this Math StackExchange answer](https://stats.stackexchange.com/a/20230/261782). Below slightly extends the answer by using (imo) a bit easier linear algebra.

![Derive (3.11)](/assets/esl/3.11.jpg)

# (3.12) Hypothesis testing of one parameter coefficient

The "Z-score" in (3.12) is a [T-statistic](https://en.wikipedia.org/wiki/T-statistic), because we don't know the population mean nor standard deviation; we are estimating from a sample.

TODO: Derive that T-statistic takes T-distribution.

Chapter 4 from *Econometric Theory and Methods* by Davidson and Mackinnon provides a self-contained explanation of hypothesis testing in linear regression models. Specifically, see section 4.4.



