---
layout: page
title: 7.3 The Bias-Variance Decomposition - Exercises
permalink: /esl/07_03_Exercises/
chapter_title: 7 Model Assessment and Selection
section_title: 7.3 The Bias-Variance Decomposition
type: Exercises
usemathjax: true
---

* toc
{:toc}

### 7.2

We will abbreviate by removing $x_0$ from $f(x_0), \hat{f}(x_0), G(x_0)$, and $\hat{G}(x_0)$.

*Show (7.62)*

Let $\hat{g} = Pr(\hat{f} > \frac{1}{2})$. Then

$$Err(x_0) = E[I[Y \neq \hat{G}] \lvert X = x_0] = Pr(Y \neq \hat{G} \lvert X = x_0) = f (1 - \hat{g}) + (1-f) \hat{g} = f - 2 f \hat{g} + \hat{g}$$

$$
Err_B(x_0) + \lvert 2f - 1 \rvert P(\hat{G} \neq G \lvert X = x_0) =
\begin{cases}
f + (1 - 2f) \hat{g} & \text{if } f \leq \frac{1}{2} \\
(1 - f) + (2f - 1) (1 - \hat{g}) & \text{else}
\end{cases} 
= f - 2 f \hat{g} + \hat{g}
$$

*Show (7.63)*

$$ Pr(\hat{G} \neq G \lvert X = x_0) = Pr(\hat{f} > \frac{1}{2})Pr(f \leq \frac{1}{2}) + Pr(\hat{f} \leq \frac{1}{2})Pr(f > \frac{1}{2})$$

If $f > \frac{1}{2}$, above reduces to $Pr(\hat{f} \leq \frac{1}{2})$. Since $\frac{\hat{f} - E[\hat{f}]}{\sqrt{Var[\hat{f}]}} \sim N(0,1)$, we obtain $Pr(\hat{f} \leq \frac{1}{2}) = \Phi(\frac{\frac{1}{2} - E[\hat{f}]}{\sqrt{Var[\hat{f}]}})$. Then, (7.63) holds because sign($\frac{1}{2} - f$) is negative. Similar (sign-reversed) argument holds for the $f \leq \frac{1}{2}$ case.