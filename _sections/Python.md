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

##### Example on Linux

    # Download the miniconda installer 
    wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh

    # Run the installer
    bash Miniconda3-latest-Linux-x86_64.sh

The default install location will be "/home/<user_name>/miniconda3" (replace <user_name> with your user name). The installer also provides the possibility to add the binairies to the path, but it defaults to not doing so. Adding conda to the path can be done by:

    # Add to path
    echo ". /home/<user_name>/miniconda3/etc/profile.d/conda.sh" >> ~/.bashrc

This change will take effect the next time you open a terminal

To test your conda installation, make a list of the installed packages and update conda to the latest version.

    # Package list
    conda list

    # Update conda
    conda update conda

The following steps will change the default channel to the Intel distribution for Python channel. These steps can be skipped.

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
    cd /home/<user_name>/miniconda3/envs/nutils
    git clone https://github.com/nutils/nutils.git
    cd nutils
    python setup.py install

    # Run the unit tests of Nutils
    cd /home/<user_name>/miniconda3/envs/nutils/nutils/tests
    python -m unittest

    # deactivate the nutils virtual environment
    conda deactivate

    

