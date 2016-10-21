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

I'll need to write a custom boundary condition within the Monte Python code. I've put the following snippet in the `get_new_position` function in `mcmc.py`.

```python
# check a special condition for two amplitude isocurvature
# check pri1
if( 'P_{RI}^1' in parameter_names ):
    # set up temporary variables so code is readable
    pri1 = vector_new[parameter_names.index('P_{RI}^1')]
    pii1 = vector_new[parameter_names.index('P_{II}^1')]
    prr1 = vector_new[parameter_names.index('P_{RR}^1')]

    # equation 128 of Planck 2015 XX
    if (abs(pri1)/math.sqrt(pii1*prr1)>1):
        flag += 1 # we're not moving here.
```

We also add the following to after line 795 of `data.py`, to ensure we also satisfy equation 129 of Planck 2015 XX. This defines $\mathcal{P}_{RI}^2$ as a derived parameter,

$$ \mathcal{P}_{RI}^2 = \mathcal{P}_{RI}^1 \frac{ \sqrt{ \mathcal{P}_{II}^2 \mathcal{P}_{RR}^2 } } { \sqrt{\mathcal{P}_{II}^1 \mathcal{P}_{RR}^1}} .$$

```python
elif elem == 'P_{RI}^1':
    self.cosmo_arguments['|P_{RI}^2|'] = abs(self.cosmo_arguments['P_{RI}^1']) * \
        math.sqrt( self.cosmo_arguments['P_{II}^2'] * self.cosmo_arguments['P_{RR}^2'] ) / \
        math.sqrt( self.cosmo_arguments['P_{II}^1'] * self.cosmo_arguments['P_{RR}^1'] )
    # this is from Planck Inflation paper 2015
```