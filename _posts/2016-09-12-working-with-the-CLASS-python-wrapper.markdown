---
title:  "Working with the CLASS python wrapper"
date:   2016-09-12 19:26:00
categories: [class]
tags: [class]
---
**Update:** *After testing this on my office computer, it looks my problems were unique to my laptop's Python configuration. It shouldn't happen for most users.*

Getting the Python wrapper to work with [CLASS][classcode] takes a little off roading, but it's an easy adventure. After downloading the code, I used `make all` to produce all of the library files. However, because I'm using Anaconda on Linux, the math library `m` is not automatically linked. In setup.py, I had the following block:

```python
setup(
    name='classy',
    version=VERSION,
    description='Python interface to the Cosmological Boltzmann code CLASS',
    url='http://www.class-code.net',
    cmdclass={'build_ext': build_ext},
    ext_modules=[Extension("classy", ["classy.pyx"],
                           include_dirs=[nm.get_include(), "../include"],
                           libraries=["class", "m"],
                           library_dirs=["../", GCCPATH],
                           extra_link_args=['-lgomp'],
                           )],
    data_files=(('bbn', ['../bbn/sBBN.dat']),)
)
```
The critical line is the one with `libraries=["class", "m"],`, instead of the original `libraries=["class"]`.

After a quick `cd python` I then ran as instructed

```
python setup.py build
python setup.py install --user
```
and after testing with `nose`, 


```
nosetests test_class.py
```

I was finally satisfied with how the python wrapper was behaving. The next step is using [Monte Python][montepython] (cosmologists just LOVE names which are difficult to Google) with CLASS, and following this [lecture series][classlecture].

[classcode]: http://class-code.net/
[montepython]:http://baudren.github.io/montepython.html
[classlecture]:http://lesgourg.web.cern.ch/lesgourg/class-tour/class-tour.html
