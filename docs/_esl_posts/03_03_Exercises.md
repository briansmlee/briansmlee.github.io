---
layout: page
title: 3.3 Subset Selection - Exercises
permalink: /esl/03_03_Exercises/
chapter_title: 3 Linear Methods for Regression
section_title: 3.3 Subset Selection
type: Exercises
usemathjax: true
---

* toc
{:toc}

### 3.9

*Suppose we have N x q matrix $X_1 = Q_1 R_1$ and residual $r_1 = y-\hat{y_1}$. Among the remaining $p - q$ features, which one should we select as $x_2$ so that the $RSS_2$ is reduced the most?*

$$ \begin{align*}
RSS_2 &= \lVert y - \hat{y_2} \rVert^2\\
&= \lVert y - Q_2 {Q_2}^T y \rVert^2 && \text{from (3.33)}\\
&= y^Ty - 2 y^T Q_2 {Q_2}^T y + y^T Q_2 {Q_2}^T Q_2 {Q_2}^T y\\
&= y^Ty - y^T Q_2 Q_2^T y && \text{(*)}\\
&= y^Ty - y^T Q_2 {Q_2}^T y\\
&= y^Ty - y^T (Q_1 Q_1^T + q_2 {q_2}^T) y && UV^T = u_1{v_1}^T + u_2{v_2}^T + ...\\
&= RSS_1 - y^T q_2 {q_2}^T y && \text{from (*)}\\
\end{align*} $$

Hence, $\arg\min_{q_2} RSS_2 = \arg\max_{q_2} y^T q_2 {q_2}^T y = \arg\max_{q_2} \lvert y^T q_2 \rvert$.

Moreover, $y = r_1 + \hat{y_1}$ and $q_2 = x_2 - Q_1{Q_1}^T x_2$ because $q_2$ is the residual after projecting $x_2$ onto $C(X_1)$. So:

$$ \begin{align*}
y^T q_2 &= (r + Q_1{Q_1}^Ty)^T (x_2 - Q_1{Q_1}^Tx_2)\\
&= r^Tx_2 - r^T Q_1{Q_1}^Tx_2 + y^TQ_1{Q_1}^T x_2 - y^TQ_1{Q_1}^T Q_1{Q_1}^Tx_2\\
&= r^T (I - Q_1{Q_1}^T) x_2\\
\end{align*} $$

Hence, we can pre-compute the fixed $r^T (I - Q_1{Q_1}^T)$ and select the $x_2$ that maximizes the absolute dot product.

### 3.10
