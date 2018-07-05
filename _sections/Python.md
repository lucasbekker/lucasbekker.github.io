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

##### Example on Linux/MacOSX

    # Download the miniconda installer 
    (linux)  wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
    (macosx) wget https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh

    # Run the installer
    (linux)  bash Miniconda3-latest-Linux-x86_64.sh
    (macosx) bash Miniconda3-latest-MacOSX-x86_64.sh

The default installation location will be "~/miniconda3". The installer also provides the possibility to add the binairies to the path, but it defaults to not doing so (for a good reason). Adding conda to the path should be done by:

    # Add to path
    (linux)  echo ". /home/<user_name>/miniconda3/etc/profile.d/conda.sh" >> ~/.bashrc
    (macosx) echo ". ~/miniconda3/etc/profile.d/conda.sh" >> ~/.bash_profile

This change will take effect the next time you open a terminal.

To test your conda installation, make a list of the installed packages and update conda to the latest version.

    # Package list
    conda list

    # Update conda
    conda update conda
    conda update --all

The following steps will change the default channel to the Intel distribution for Python channel. These steps should be skipped for maximum compatibility.

    conda config --add channels intel
    conda update --all


##### Installation of Nutils

The following serves as an example of the workflow using conda.

    # Create a new Python virtual environment, best practise is to create a new environment for every project.
    conda create --name nutils python=3

    # Activate the new environment (on Windows, 'activate nutils')
    conda activate nutils

    # Install the nutils requirements
    conda install matplotlib numpy scipy sphinx

    # Install Nutils
    cd ~/miniconda3/envs/nutils
    git clone https://github.com/nutils/nutils.git
    cd nutils
    python setup.py install

    # Run the unit tests of Nutils
    cd ~/miniconda3/envs/nutils/nutils
    python -m unittest

    # deactivate the nutils virtual environment
    conda deactivate

### CUDA development in Python

CUDA development in Python focusses on two different approaches. The first tries to integrate GPU programming into Python with minimal additional code and dificulty. The aim of this approach is to provide (most of) the power of GPU's to the avarage Python developer in an almost automated maner.
The second approach is to provide what is basically a wrapper for the CUDA toolkit. This unleashes the full power of CUDA to the Python developer, but sacrifices ease of use for performance and features.

#### Numba

[Numba](https://numba.pydata.org/) falls into the first catagory of CUDA Python development. The basic idea behind Numba is to perform a [Just-In-Time](https://en.wikipedia.org/wiki/Just-in-time_compilation) (JIT) compilation step for sections of code before they are executed. Numba uses the [LLVM](https://llvm.org/) compiler infrastructure to generate optimized machine code, and as such is not limited to CUDA.

#### PyCUDA

[PyCUDA](https://mathema.tician.de/software/pycuda/) falls in the second catagory.