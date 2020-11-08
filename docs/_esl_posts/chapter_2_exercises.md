---
layout: page
title: 2.3 Least squares and Nearest Neighbors - Exercises
permalink: /esl/02_03_Exercises/
chapter: 02_03
chapter_title: 2.3 Least squares and Nearest Neighbors
type: Exercises
usemathjax: true
---

# 2.1

(I will write the prediction $$\hat{y}$$ as $$y$$.)

$$argmin_k \lvert\lvert t_k - y \lvert\lvert = argmin_k (t_k - y)^T (t_k - y) = argmin_k [{t_k}^T t_k - 2 y^T t_k + y^Ty]$$.

$${t_k}^T{t_k}$$ is 1 for any $$k$$ and $$y^Ty$$ is not affected by $$k$$. So, the problem is equivalent to $$argmax_k [y^T t_k]$$, which picks the position in $$y$$ with the largest element.

