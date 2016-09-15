---
title:  "Testing Monte Python"
date:   2016-09-14 21:13:00
categories: [class]
tags: [class]
---

For these exploratory Markov Chain chains, I'm using a fake likelihood function generated from the Planck blue book. Running the example parameter configuration (many free cosmological parameters to fit) for a relatively low number of cycles, we can see the beginnings of some interesting posterior distributions.

![Low N Triangle Plot]({{ site.baseurl }}images/monte_first_plot.png)

However, I think it's especially cool just to see the text output when I only allow one free parameter (latest Planck measurements fix the other parameters), the value of `h`.


<div style="color:blue">

```
Running Monte Python v2.2.2

with CLASS v2.5.0
 /!\ Detecting empty folder, logging the parameter file

Testing likelihoods for:
 -> fake_planck_bluebook

Initialised likelihood_mock_cmb with following options:
  unlensed_clTTTEEE is False
  Bmodes is False
  delensing is False
  LensingExtraction is False
  neglect_TD is True

Creating chains/planck/only_H/2016-09-14_5000__1.txt


Deduced starting covariance matrix:
['h']
[[  4.22e-05]]

#  -LogLkl	h               
3  3324.27	7.027504e-01	
1  318.933	6.800817e-01	
3  113.887	6.669130e-01	
3  89.4986	6.678106e-01	
16  50.2757	6.705897e-01	
46  48.9665	6.711500e-01	
8  49.2896	6.708960e-01	
36  49.281	6.709005e-01	
73  50.0006	6.706602e-01	
10  50.5039	6.705405e-01	
36  49.6986	6.716817e-01	
8  49.2723	6.709070e-01	
7  49.6086	6.707709e-01	
51  49.5382	6.716285e-01	
56  49.9748	6.717597e-01	
14  49.3748	6.715667e-01	
2  48.9348	6.712112e-01
```
</h1>

It's pretty cool to see the value of `h` converge to roughly 0.67 and also see the log-likelihood decrease, as the chain explores the parameter space.

