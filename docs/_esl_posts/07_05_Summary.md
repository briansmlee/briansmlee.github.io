---
layout: page
title: 7.5 Estimates of In-Sample Prediction Error - Summary
permalink: /esl/07_05_Summary/
chapter_title: 7 Model Assessment and Selection
section_title: 7.5 Estimates of In-Sample Prediction Error
type: Summary
usemathjax: true
---

$$\hat{Err}_{in} = \overline{err} + \hat{w}$$. If squared error loss, we obtain $$C_p = \overline{err} + 2 \frac{d}{N} \hat{\sigma}^2_\varepsilon$$. Use MSE of a low-bias model for $$\hat{\sigma}^2_\varepsilon$$.

If log-likelihood loss, another estimate of $Err_{in}$ is $$ AIC = \frac{2}{N} (- logik + d)$$. For Gaussian model, AIC is equivalent to $C_p$.

 If $d$ basis functions are chosen adaptively from $p$ inputs, effective number of parameters is more than $d$. 

 For nonlinear models, replace $d$ with some measure of model complexity.

 TODO: (7.30) formulation of AIC.