---
layout: default
title: "Basic computer hardware concepts"
--- 

### Performance analysis

GPGPU acceleration of mathematical problems centers around runtime performance. Enhancing the performance of a software routine becomes easier if certain basic concepts about computer hardware are familiar. The best performance can only be acchieved if the (machine) code is tailord towards the hardware on which the code will be executed.

Basic hardware concepts, and a couple of more advanced ones, will be discussed using a few examples.

#### Tradional computer model

The traditional computer was designed to perform many different operations on a relatively small amount of data. Because parallelising many different operations on the same data is very hard (or impossible), sequential execution of the operations has long been (still is) the norm. The result is a combination of a few very fast execution units (in the CPU) and a "pyramid shaped" memory/storage system. 

![Piramid](../image/Traditional-computer.png){:width="600px"}

##### Pyramid shape

Creating fast memory is expensive and not all the available data needs to be instantly accessable. Production cost savings led to a small amount of very fast memory close to the execution units, called "Cache". A larger amount of significantly slower memory, called "RAM", acts as the data overflow buffer of the cache. The lowest layer of memory consistes of non-volitile storage, often in the form of an HDD or SSD, which contains the data that the needs to survive a power cycle.

As CPU's grew more capable, and the way in which they where used, changed over the years, additional layers (L2 and L3) of cache where added to accomodate.

##### Bandwidth

Bandwidth is one of two measures of the "speed" of memory, but bandwidth is a broader concept. Bandwidth is a measure of the (maximum) amount of data that can be transferred between a sender and a receiver within a timeframe. Data transfer channels are usually bi-directional, making the distinction between sender and receiver less relevant.

High data transfer rates are desirable, but like storage capacity, are costly to achieve. The traditional computer model benefits most from high memory bandwidth at the cache level and it becomes less important towards the bottom of the "pyramid".

The most common measure for bandwidth is bytes per second, a table of derived units and their meaning is provided below. (A bit is a single one or zero and a byte is a set of 8 bits)

| kilo  | mega  | giga  | terra | bit/byte per second                                                |
|:------|:-----:|:-----:|:-----:|:-------------------------------------------------------------------|
|       |       |       |       |                                                                    |
| Kb/s  | Mb/s  | Gb/s  | Tb/s  | 1.000 - 1.000.000 - 1.000.000.000 - 1.000.000.000.000 bits/second  |
| KB/s  | MB/s  | GB/s  | TB/s  | 1.000 - 1.000.000 - 1.000.000.000 - 1.000.000.000.000 bytes/second |
| Kib/s | Mib/s | Gib/s | Tib/s | 1.024 - 1.048.576 - 1.073.741.824 - 1.099.511.627.776 bits/second  |
| KiB/s | MiB/s | GiB/s | TiB/s | 1.024 - 1.048.576 - 1.073.741.824 - 1.099.511.627.776 bytes/second |

#### CPU

![CPU](../image/CPU+Legend.png){:width="600px"}

This example CPU is the [Intel Xeon E5-2667v3](https://ark.intel.com/products/83361/Intel-Xeon-Processor-E5-2667-v3-20M-Cache-3_20-GHz). 

It contains:

 - 8 cores and 16 threads.
 - 20 MB L3 cache
 - 40 PCI-e 3.0 lanes
 - Quad channel DDR4 ECC memory controller
 - 2 QPI 9.6 GT/s links

The CPU is the "beating heart" of a computer, and as such, performes many more tasks than the ones that will be discussed here. The focus lies on the floating point calculation capabilities and the memory subsystems, as well as the interfaces.