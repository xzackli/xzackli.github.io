---
title:  "Need to Write a New Monte Python Prior"
date:   2016-10-20 19:22:00
categories: [class]
tags: [class]
---

I'm having some issues reproducing the Planck 2015 result. I spent the last few weeks learning QFT and some MCMC diagnostics. QFT started taking up all of my time, so I had to drop the class. I'll pick up the material later. 

I'm getting an error message to due a condition described in the Planck 2015 XX, equation 129,

$$ \frac{ \mathcal{P}_{RI} }{ \sqrt{ \mathcal{P}_{RR} \mathcal{P}_{II} } } \in (-1,1). $$

~~~~~~
Cosmological Module Error:
 /|\   Something went wrong when calling CLASS
/_o_\  Error in Class: input_init(L:402) :error in
       input_read_parameters(&(fzw.fc), ppr, pba, pth, ppt, ptr, ppm, psp, pnl,
       ple, pop, errmsg);
       =>input_read_parameters(L:1552) :condition (fabs(pri1)/sqrt(pii1*prr1)>1)
       is true; too large ad-iso cross-correlation in k1
~~~~~~

This will have to be implemented with a custom prior within the Monte Python code.

