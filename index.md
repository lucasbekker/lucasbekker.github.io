# Documentation

Welcome to the documentation of my master thesis project software.

### Repository

The source code of the master thesis project can be found at:
[Master Thesis Project](https://github.com/lucasbekker/Master-Thesis-Project)

The source code of the documentation can be found at:
[Documentation](https://github.com/lucasbekker/lucasbekker.github.io)

### CUDA installation

The following information is to be considered complementary to the documentation that NVIDIA provides. Users who don't have a whole lot of experience with the CUDA toolkit, or are otherwise unfamiliar with the installation process, might find useful information.

Regarding the linux section, users on distributions other than Ubuntu, might be of the opinion that the following text is biased towards Ubuntu. The recommendations that follow are based on my personal experience, and as such may very well be biased. (contributions are always welcome)

#### Linux

Installing CUDA on linux can be cumbersome, if you don't stick to the officially supported distributions. These vary according to the CUDA toolkit version you wish to install. A list of supported linux distributions for CUDA 9.1 can be found [here](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#system-requirements). The following is a list of linux distributions that NVIDIA supports on AMD64 capable hardware:

  * CUDA 9.1 supports Fedora 25, OpenSUSE 42.3, SLES 12 SP3, RHEL/CentOS 7 and 6, Ubuntu 16.04 LTS and 17.04.
  * CUDA 8.0 supports Fedora 23, OpenSUSE 13.2, SLES 12 and 11 SP4, RHEL/CentOS 7 and 6, Ubuntu 16.04 LTS and 14.04 LTS.
  * CUDA 7.5 supports Fedora 21, OpenSUSE 13.2, SLES 12 and 11 SP3, RHEL/CentOS 7 and 6, Ubuntu 15.04 and 14.04 LTS.
  * CUDA 6.0 supports Fedora 19, OpenSUSE 13.2, SLES 11 SP3 and SP2, RHEL/CentOS 6 and 5, Ubuntu 13.04 and 12.04 LTS.

Another possibility is to use a prepackaged version of CUDA, generally provided by the linux distribution itself. Debian 8 (jessie) is a good example of a linux distribution that is not officially supported by NVIDIA, but does provide a prepackaged CUDA toolkit in the backports repository.

Even if a prepackaged CUDA toolkit is available for your distribution, it might be better to use a version provided by NVIDIA. Ubuntu 16.04 LTS is an officially supported distribution for a number of CUDA toolkit versions, but also provides a prepackaged version of CUDA 7.5. It might be tempting to just install the prepackaged version ( `sudo apt install nvidia-cuda-toolkit` ), but the way in which certain libraries are provided deviates from the official NVIDIA way, which may cause problems later on.

##### Compiler

An important aspect of the prerequisites of the CUDA toolkit is the supported c/c++ compiler (not only on linux). This also varies from version to version of CUDA and can be found in the same table that also provides the officially supported linux distributions.

GCC support of CUDA:

  * CUDA 9.1 supports gcc up-to 6.x
  * CUDA 8.0 supports gcc up-to 5.x
  * CUDA 7.5 supports gcc up-to 4.x
  * CUDA 6.0 supports gcc up-to 4.7

The gcc compiler and linux distributions are heavily intertwined. You could install (or compile) a different version of gcc on your distribution, but you would also need to install or recompile various libraries to ensure ABI compatibility. Ubuntu LTS releases usually provide prepackaged versions of older gcc compilers in their repositories, which can be used for this purpose:

    sudo apt install gcc-4.9 g++-4.9
    
    sudo ln -s /usr/bin/gcc-4.9 /usr/local/cuda/bin/gcc
    sudo ln -s /usr/bin/g++-4.9 /usr/local/cuda/bin/g++

The above commands install gcc 4.9 on Ubuntu 16.04 LTS and links that to the installed CUDA toolkit. This (and similar) solutions have been reported to work correctly, but your results may vary.

##### Toolchain

A reliable and well documented toolchain is paramount to software development. Achieving this doesn't have to be difficult, but it does limit the options somewhat.

Choosing the right linux distribution is an important step, because it determines the (system default) compiler, libraries and available support. Ubuntu LTS releases are safe choices, because they are a common target for third party vendors of linux compatible software, have a broad community and good documentation. Other distributions, like CentOS, are also viable alternatives, but tend to be more problematic. This can usually be contributed to libraries and packages being too old or too new. 

##### Ubuntu and derivatives

Ubuntu 16.04 LTS is a good choice for linux development in general and CUDA development as well. The system default compiler is gcc 5.4, which is officially supported by the CUDA toolkit versions 8.0 and 9.x (possibly later versions too). The availability of the Hardware Enablement (HWE) stack provides the choice between a rock solid linux 4.4 LTS kernel and a more recent kernel for those who need or want it.

Ubuntu 16.04 LTS is an officially supported linux distribution for the versions 8.x and 9.x. NVIDIA does not officially support Ubuntu 16.04 for CUDA 7.5, but as mentioned earlier, a prepackaged version of CUDA 7.5 is available in the official Ubuntu repositories.

An other advantage of the 16.04 LTS release is that it is supported until sometime in 2021, and even longer support is available for paying customers. Not having to reevaluate the toolchain and development environment every year is a big plus.

Derivatives of Ubuntu LTS releases, like for example Kubuntu 16.04, are similar enough to cause minimal difficulties. The only real exception to this are window managers (kwin, mutter, compton) and their interaction with NVIDIA proprietary drivers. Certain third party software is known to produce more segmentation faults if the graphics stack is not completely standard, and a different window manager can cause problems.

##### CUDA toolkit version

If your project doesn't require the latest and greatest features of the CUDA toolkit, it might be advantageous to stick to an earlier version of CUDA. version 8.0 has hardware support for the Fermi, Kepler, Maxwell and Pascal architectures (newer versions removed Fermi support in favor of Volta and older versions lack Pascal support).

##### NVIDIA graphics driver

Installing the proprietary NVIDIA graphics driver on linux can be a hassle, requiring kernel header files, dkms and compiler. A further complication is that certain installation methods require the manual blacklisting of the open source and unofficial NVIDIA driver (nouveau). Various linux distributions have made a lot of progress over the last couple of years in aiding the user in the installation of the NVIDIA graphics driver, but the installation of the CUDA toolkit also installs the driver that NVIDIA recommends (this behavior can be altered).

My personal recommendation would be to stick to the defaults that NVIDIA provide. The installation instructions included in the CUDA toolkit documentation are easy to follow and tell the user how to prepare the system for the CUDA toolkit as well as the included graphics driver.

A last note on the graphics driver is that the CUDA toolkit requires a minimum version, which depends on the version of the toolkit. The by NVIDIA included driver will always meet that requirement, but if you decide to manually force a different version of the graphics driver, you will have to take this into account.

#### Docker

[NVIDIA Docker](https://devblogs.nvidia.com/nvidia-docker-gpu-server-application-deployment-made-easy/) is a relatively new development that aims to facilitate running CUDA applications and development in a containerized world. It can also be used to setup a CUDA development environment with relative ease. (only supported on linux)

GPGPU acceleration in a containerized environment has the inherent problem that containerized environments are by design hardware agnostic, limiting access to the GPU. NVIDIA provides software for Docker that circumvents this problem, called `nvidia-docker2`. The host operating system requires a supported NVIDIA graphics driver, Docker and the aforementioned `nvidia-docker2`, The CUDA toolkit and other user space software runs inside the container. A list of [prerequisites](https://github.com/NVIDIA/nvidia-docker/wiki/Installation-(version-2.0)#prerequisites) and a [quick installation guide](https://github.com/NVIDIA/nvidia-docker) are available.

One of the prerequisites is a CUDA capable device of an architecture newer than Fermi, meaning: Kepler, Maxwell, Pascal and Volta (at the time of writing). Even though CUDA 8.0 and earlier development environments are available using NVIDIA Docker, targeting Fermi and Tesla will not be possible using NVIDIA Docker.

NVIDIA docker Installation instructions:

    # Install docker (provided by Canonical) and curl
    sudo apt install docker.io curl

    # Add the NVIDIA docker repository to the system
    curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
    distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
    curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
    sudo apt update

    # Install nvidia-docker2 and reload the Docker daemon configuration
    sudo apt install nvidia-docker2
    sudo pkill -SIGHUP dockerd

    # Add the user to the docker group (logoff and login to take effect)
    sudo usermod -aG docker "username"

    # Test NVIDIA docker with nvidia-smi
    docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi

##### Example

As an example, the following command will open an interactive shell in a CUDA 8.0 development environment Docker container:

    docker run -it --runtime=nvidia --rm nvidia/cuda:8.0-devel /bin/bash

Running `nvcc -V` and `gcc --version` in this bash prompt results in:

    nvcc: NVIDIA (R) Cuda compiler driver
    Copyright (c) 2005-2016 NVIDIA Corporation
    Built on Tue_Jan_10_13:22:03_CST_2017
    Cuda compilation tools, release 8.0, V8.0.61

    gcc (Ubuntu 5.4.0-6ubuntu1~16.04.9) 5.4.0 20160609
    Copyright (C) 2015 Free Software Foundation, Inc.
    This is free software; see the source for copying conditions.  There is NO
    warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

As can be seen from these results, NVIDIA made the decision to base their Docker container on Ubuntu 16.04 LTS

### Julia

#### CUDA accelerated Julia 

##### Installation using docker

NVIDIA provides a docker container that contains everything you need to start with CUDA accelerated Julia.

Install NVIDIA docker: [Instructions](https://lucasbekker.github.io/#docker)

    # Pull the docker container
    docker pull maleadt/juliagpu

    # Create the data and packages directories
    mkdir JuliaGPU JuliaGPU/data JuliaGPU/pkg
    
    # Create alias for ease of use (could be added to ~/.bashrc)
    PKG='JuLiaGPU/pkg'
    DATA='JuliaGPU/data'
    alias juliagpu='docker run --runtime=nvidia -v $PKG:/pkg -v $PWD:/data -it maleadt/juliagpu'


### Background

Simulations based on the Boltzmann or Navier-Stokes Cahn-Hilliard equations are complex and multifaceted. The part that will be accelerated using GPGPU techniques is the solving of systems of non-linear equations.

#### Bilinear form

The weak and discretized formulations of the Boltzmann and Navier-Stokes Cahn-Hilliard equations can be abstracted to the following:

$$
\begin{array}{lr}
a( \sum_{j=1}^{m} u_{k}^{j} \psi_{j} ; \psi_{i} ) = f(\psi_{i}) & \forall i \in \left [ 1,m \right ]
\end{array}
$$

  * $a(\cdot \, ; \cdot)$ is the bilinear form.
  * $u_{k}^{j}$ is the solution at time $k$, on location $j$.
  * $\psi_{i}$ is the i *th* test function.
  * $m$ is the total amount of test functions.

Which can be expressed by the following system of non-linear equations:

$$
N(\underline{u_{k}}) = \underline{f}
$$

With $\underline{u_{k}} = \left [ u_{n}^{1} \,,u_{n}^{2} \,,...\,,u_{n}^{m} \right ]$.

This system of non-linear equations needs to be solved for every time step, using the Newton-Raphson method.

#### Newton's method

Applying Newton's method for timestep $k$ results in the following system:

$$
J_{N}(u_{k,n}) (u_{k,n+1} - u_{k,n}) = - N(u_{k,n}) + f
$$