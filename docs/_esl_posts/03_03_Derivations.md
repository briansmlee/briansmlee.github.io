---
layout: page
title: 3.3 Subset Selection - Derivations
permalink: /esl/03_03_Derivations/
chapter_title: 3 Linear Methods for Regression
section_title: 3.3 Subset Selection
type: Derivations
usemathjax: true
---

* toc
{:toc}

### (p57) Best-subset curve is necessarily decreasing, so we cannot use RSS to select the subset size.

Since RSS is the residual after projecting y onto the $C(X)$, RSS decreases as we expand $C(X)$ with larger subsets.

### (p59) Forward stepwise will have lower variance than best subset

(Hand-wavy) Forward stepwise simply has less features to choose from at each size since it's greedy.

### (p60) Selection by F-statistics do not account for multiple testing issues

### (p60) Standard errors after the model search is not valid, because they do not account for the search process.
