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

Memory latency is a highly multifaceted topic, which is largely beyond the scope of this text, but should be understood at a global level to appreciate the performance impact on certain algorithms. Latency, or access time, is defined as the amount of time between a request to a system and the response of the system. Memory latency is the second important measure of the "speed" of memory.

In order to understand memory access time, one must first (roughly) understand how memory is accessed. Computer memory is a highly structured and complex system, with many different layers and subsystems (cache, RAM, HDD). The steps that are required to access data from computer memory are dictated by the structure of the global computer memory system, but also by the local structure of the memory subsytem that contains the data. These local structures can vary pretty significantly from subsystem to subsystem, but they all "group" their resources into "memory blocks", which contain the actual data. The nature of these "blocks" is definded by the precise structure of the specific memory subsystem.

When the user makes a request to access certain (parts) of data, a list of "storage adresses" is generated. This list of "storage adresses" maps to the memory subsystem and corresponding memory blocks that contain the requested data. This list of storage adresses is passed through to the relevant memory subsystem and then gets processed. This results in the data contained in the memory blocks being presented to one or more of the outputs of the memory subsystem in a serial fashion.

The time between the arrival of the storage adresses list and the moment the first block of data is presented, is called latency of that memory subsystem. The total latency of a data access request is the amount of time from the moment a "gather" instruction is issued till the moment that the data is "gathered" (available for manipulation). 

Latency is usually measured in mili/nano seconds, but can also be provided in cycles. This is totally equivalent to time, because each cycle takes a set amount of time (dependant on operating frequency).