---
layout: default
title: "Hardware"
--- 

### Performance analysis

GPGPU acceleration of mathematical problems centers around runtime performance. Enhancing the performance of a software routine becomes easier if certain basic concepts about computer hardware are familiar. The best performance can only be acchieved if the (machine) code is tailord towards the hardware on which the code will be executed.

Basic hardware concepts, and a couple of more advanced ones, will be discussed using a few examples:

#### Dual socket, quad GPU compute node

![Block diagram](../image/blok-diagram.png){:width="1000px"}

A high level block diagram of a dual socket, quad GPU, compute optimized rack server from around 2014/2015. The two CPU's (Central processing Units) are Intel Xeon units from the Haswell/Broadwell generation. The four GPU's are NVIDIA Tesla K40 units, from the Kepler generation.

This specific example was chosen because it uses some of the first hardware that was really targeted at (double precision) High Perfomance Computing (HPC), contains enough complexity to accurately represent typical GPGPU compute nodes, but stil resembles consumer hardware at the fundamental levels.

##### CPU

![CPU](../image/CPU+Legend.png){:width="500px"}

This example CPU is the [Intel Xeon E5-2667v3](https://ark.intel.com/products/83361/Intel-Xeon-Processor-E5-2667-v3-20M-Cache-3_20-GHz). 

It contains:

 - 8 cores and 16 threads.
 - 20 MB L3 cache
 - 40 PCI-e 3.0 lanes
 - Quad channel DDR4 ECC memory controller
 - 2 QPI 9.6 GT/s links

The CPU is the "beating heart" of a computer, and as such, performes many more tasks than the ones that will be discussed here. The focus lies on the floating point calculation capabilities and the memory subsystems, as well as the interfaces.