---
title:  "Planck 2013 Inflation Constraints"
date:   2016-09-27 20:30:00
categories: [class]
tags: [class]
---

[Planck](http://arxiv.org/abs/1303.5082) parametrizes isocurvature in a pretty reasonable way. We assume that the adiabatic, isocurvature, and cross-corrrelation power spectra obey power laws with some index $n$. 

> Question 
>> Why does one expect power spectra of isocurvature to exhibit near scale invariance?

How do you parametrize a power law? The standard way, 
$$f(x) = ax^b$$
chooses a pivot scale (0 in this case) and normalization $a$. The Planck collaboration chose not to use this method due to some mysterious Bayesian reasons (something about a prior). Instead, we specify the power $\mathcal{P}_{ab}$ at two scales $k = k_1$ and $k=k_2$, interpolating in a specific way,
$$ \mathcal{P}_{ab}(k) = \text{exp} \left[ \left( \frac{\ln(k) - \ln(k_2)}{\ln(k_1) - \ln(k_2) } \right) \ln( \mathcal{P}^(1)_{ab} ) +  left( \frac{\ln(k) - \ln(k_1)}{\ln(k_2) - \ln(k_1) } \right) \ln( \mathcal{P}^(2)_{ab} )  \right].$$