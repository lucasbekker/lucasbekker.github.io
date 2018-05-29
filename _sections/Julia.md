---
layout: default
---

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


