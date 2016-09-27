---
title:  "Summarizing CLASS isocurvature"
date:   2016-09-27 13:35:00
categories: [class]
tags: [class]
---
I spent all weekend on my seminar talk on extragalactic magnetic fields. It happens once per semester, but it meant I didn't get very much research done since last week.

In this post, I'm going to give a rundown of the ways one can vary isocurvature in the CLASS initial conditions. 

The first parameter for isocurvature `ic` turns on the kind of isocurvature modes we will allow. Remember that these are **isocurvature** perturbations, and thus preserve curvature while still perturbing primordial components. These arise from the three isocurvature modes when varying \\(\delta_{\gamma}, \delta_{\nu}, \delta_b, \delta_c \\).


```
7) list of initial conditions for scalars ('ad' for adiabatic, 'bi' for baryon
   isocurvature, 'cdi' for CDM isocurvature, 'nid' for neutrino density
   isocurvature, 'niv' for neutrino velocity isocurvature). More than one of
   these allowed, can be attached or separated by arbitrary characters; letters
   can be small or capital.
   (default: set to 'ad')

ic = ad
#ic = ad&bi&nid
```

Next, we can prescribe the entropy-to-curvature ratio for each mode.

```
2.a.3) isocurvature/entropy perturbations: for each mode xx ('xx' being one of
       'bi', 'cdi', 'nid', 'niv', corresponding to baryon, cdm, neutrino
       density and neutrino velocity entropy perturbations), enter the
       entropy-to-curvature ratio f_xx, tilt n_xx and running alpha_xx, all
       defined at the pivot scale; e.g.  f_cdi of 0.5 means S_cdi/R equal to
       one half and (S_cdi/R)^2 to 0.25
       (default: set each 'f_xx' to 1, 'n_xx' to 1, 'alpha_xx' to 0)

f_bi = 1.
n_bi = 1.5

f_cdi=1.

f_nid=1.
n_nid=2.
alpha_nid= 0.01

etc.
```


We then specify the isocurvature amplitude.

```
2.e.3) if one isocurvature mode has been turned on ('ic' set e.g. to 'ad,cdi'
       or 'ad,nid', etc.), enter values of the isocurvature amplitude
       'P_{II}^1', 'P_{II}^2', and cross-correlation amplitude 'P_{RI}^1',
       '|P_{RI}^2|' (see Planck paper on inflation for details on definitions)

P_{II}^1 = 1.e-11
P_{II}^2 = 1.e-11
P_{RI}^1 = -1.e-13
|P_{RI}^2| = 1.e-13
```


Finally, there is a setting `special_iso` for using exotic components like axions and curvatons.

```
2.e.4) set 'special iso' to 'axion' or 'curvaton' for two particular cases:
       'axion' means uncorrelated, n_ad equal to n_iso, 'curvaton' means fully
       anti-correlated with f_iso<0 (in the conventions of the Planck inflation
       paper this would be called fully correlated), n_iso equal to one; in
       these two cases, the last three of the four paramneters in 2.c.3 will be
       over-written give the input for 'P_{II}^1' (defaut: 'special_iso' left
       blanck, code assumes general case described by four parameters of 2.c.3)

special_iso =
```
