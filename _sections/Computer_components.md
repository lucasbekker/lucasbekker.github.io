---
layout: default
title: "Computer components"
--- 

#### CPU



The CPU is the "beating heart" of a computer, and as such, performes many more tasks than the ones that will be discussed in this text. The focus lies on the floating point calculation capabilities and the memory subsystems, as well as the interfaces.

Modern CPU's are very complex and multi-faceted, varying wildly with instructionset, architecture, platform and manufacturer. A discussion about the aforementioned topics for "all" CPU's would be very lengthy and diverse, necessitating a confinement. Intel dominates the PC/laptop as well as the HPC/Supercomputer CPU market, making the restriction towards an Intel x86_64 based CPU justified. Considering the fact that almost all Laptops and workstations contain CPU's that are (to a varying extend) derived from their server oriënted counterparts, focusing the discussion around a server CPU seems logical as well. The choice of architecture/generation is also important, because the differences between architectures can be substantial on many levels. Modern (at the time of writing) Intel architectures feature very significant advancements for scientific computing.

The Intel Xeon Gold 1632 will be used as an example, because it matches the criteria stated above. The second reason for choosing this particular CPU, is the fact that it is used in the new (at the time of writing) cluster available to the MEFD group at the TU/e.

##### Intel Xeon Gold 1632

![CPU](../image/Skylake-SP-Gold-1632.png){:width="800px"}

This example CPU is the [Intel Xeon Gold 1632](https://ark.intel.com/products/123541/Intel-Xeon-Gold-6132-Processor-19_25M-Cache-2_60-GHz). 

It contains:
 - 14 cores and 28 threads
 - 6 channel DDR4 ECC memory controller
 - 19.25 MiB L3 cache
 - 14 MiB L2 cache
 - 0.875 MiB L1 cache
 - 48 PCI-e v3.0 lanes
 - 2 AVX-512 FMA units per core

##### System on a Chip

Modern CPU's are best decribed by the ["System on a Chip" (SoC)](https://en.wikipedia.org/wiki/System_on_a_chip) moniker, containing many of the core components of a modern computer. As such, most contain the following subsystems:

 - Multiple cores
 - Memory controller
 - Last level cache
 - Interfaces

Consumer oriënted CPU's usually also contain a graphics subsystem.

##### 