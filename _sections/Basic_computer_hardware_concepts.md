---
layout: default
title: "Basic computer hardware concepts"
--- 

#### Traditional computer model

The traditional computer was designed to perform many different operations on a relatively small amount of data. Because parallelising many different operations on the same data is very hard (or impossible), sequential execution of the operations has long been (still is) the norm. The result is a combination of a few very fast execution units (in the CPU) and a "pyramid shaped" memory/storage system. 

![Piramid](../image/Traditional-computer.png){:width="600px"}

##### Pyramid shape

Creating fast memory is expensive and not all the available data needs to be instantly accessable. Production cost savings led to a small amount of very fast memory close to the execution units, called "Cache". A larger amount of significantly slower memory, called "RAM", acts as the data overflow buffer of the cache. The lowest layer of memory consistes of non-volitile storage, often in the form of an HDD or SSD, which contains the data that the needs to survive a power cycle.

As CPU's grew more capable, and the way in which they where used, changed over the years, additional layers (L2 and L3) of cache where added to accomodate.

##### [Bandwidth](https://en.wikipedia.org/wiki/Bandwidth_%28computing%29)

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

##### [Latency](https://en.wikipedia.org/wiki/Latency_%28engineering%29)

Latency is defined as the amount of time between a request to a system and the response of the system. Memory latency is the second important measure of the "speed" of memory.

Memory access time is a highly multifaceted topic, which is largely beyond the scope of this text, but should be understood at a global level to appreciate the performance impact on certain algorithms. In order to understand memory access time, one must first (roughly) understand how memory is accessed.

Data in computer memory is stored in "blocks". These "blocks" have a fixed size and data can span a multitude of blocks. When the user makes a request to access certain (parts) of data, a list of "storage adresses" is generated. This list of "storage adresses" maps to the memory blocks that contain the requested data.

This list of storage adresses is passed through to the memory subsystem (cache, RAM, HDD) that contains the requested data. This list then gets processed by the memory subsystem, which results in the data contained in the memory blocks being presented to the output of the memory subsystem in a serial fashion. The time between the arrival of the storage adresses list and the moment the first block of data is presented, is called "latency".

If the user has requested multiple blocks at once, the data of the next memory block is presented to the output as soon as the previous block has been gathered at the output. If the user makes multiple requests of a single block, with a slight delay in between the requests, the latency penalty has to be paid for every single request.

Latency is usually measured in mili/nano seconds, but can also be provided in cycles. This is totally equivalent to time, because each cycle takes a set amount of time (dependant on operating frequency).