---
title:  "Saha approximation for the free electron fraction"
date:   2016-11-28 12:30:00
categories: [plots]
tags: [boltzmann]
---

Here we reproduce a basic cosmological calculation. At recombination, the free electron fraction can be written

$$X_e \equiv \frac{n_e}{n_e + n_H}$$

Prior to recombination, we can use the Saha approximation to estimate the fraction $$X_e$$.

$$ \frac{X_e^2}{1-X_e} \simeq \frac{1}{n_b} \left( \frac{m_e T_b} {2 \pi} \right)^{3/2} e^{-\epsilon_0 / T_b}$$

where we approximate the baryon temperature through recombination as the photon temperature,

$$ T_b \simeq T_r = \frac{T_0}{a}.$$

We use Callin's default model.

```python
# default model, eq 16 of Callin
h = 0.7
H0 = 100 * h * 3.24077929e-20 * const.eV_of_time # 1/eV
T0 = 2.725 / const.eV_of_temp
omega_r = 5.042e-5
omega_b = 0.046
omega_m = 0.224
n = 1
Yp = 0
omega_lambda = 1 - (omega_r + omega_b + omega_m)

# baryon density 
rho_c = 3 * H0**2 / (8 * const.pi * const.G )
```

Then we can numerically solve the Saha equation using Brent's method, via scipy's `scipy.optimize.brentq`. Here, we plot the resulting calculated $$X_e$$ with a vertical line showing that at $$z \approx 1587.6$$, $$X_e = 0.99$$, which is approximately where we should stop using the Saha approximation.

![Saha approximation's X_e vs. z]({{ site.baseurl }}images/saha_Xe.png)

For the time after recombination, we instead use the Peebles equation. This is a complicated ODE, but we can solve it without much trouble.

![Peebles equation X_e vs. z]({{ site.baseurl }}images/peebles_plot.png)

