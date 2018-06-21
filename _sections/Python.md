---
layout: default
title: "Python"
--- 

### Installing Python

Depending on the operating system, python might already be installed. Even if it is, there are advantages to using a different version of Python.

#### Anaconda by Continuum

[Anaconda](https://www.anaconda.com/) advertises itself as a machine learning and data science software distribution, containing Python, R and many other packages. It's most distinguishing feature is the conda package manager, facilitating many workflow enhancements like Python virtual environments and package multi-versioning.

Python virtual environments are a great way to maintain multiple Python toolchains on a single machine, significantly reducing the project maintanance workload. A second advantage of Python virtual environments is the possibility to redistribute the toolchain as a part of the developed software, reducing package version related issues.

A specific advantage of Anaconda is the fact that it facilitates easy integration of third party libraries and binairies. Great examples would be the Intel MKL library for an accelerated LAPACK implementation and the Intel distribution for Python.

##### Installation of Anaconda

The easiest way to install Anaconda is to [download](https://conda.io/miniconda.html) the installer for miniconda, which consists of only the conda package manager. Instructions on how to install miniconda can be found [here](https://conda.io/docs/user-guide/install/index.html).

Most of the common conda commands are listed in the [conda cheat sheet](https://conda.io/docs/_downloads/conda-cheatsheet.pdf).