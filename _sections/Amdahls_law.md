---
layout: default
title: "Amdahl's Law"
--- 

### Theoretical speedup

Applying parallel programming techniques to accelerate an algorithm is a very common task. This section will discuss some of the available theory for making predictions about the maximum speedup that can be achieved.

#### Amdahl's law

[Amdahl's law](https://en.wikipedia.org/wiki/Amdahl%27s_law) relates the maximum achievable speedup of a task to the amount of time that the task executes elements that can be parallelized. This is based on two assumptions:

 - The task can be divided in a serial part and a parallel part.
 - The parallel part scales linearly with the amount of available parallel nodes.



$ T_{total} = T_{serial} + T_{parallel} $

$ Speedup(k) = \frac{T_{total}}{T_{serial} + (\frac{T_{parallel}}{k})} $

$ k $ := number of parallel nodes

As an example, take a task that consist of 95%  parallelizable work. The maximum speedup can never exceed 20, no matter how much parallel nodes are employed.

##### Parallel slowdown

[Parallel slowdown](https://en.wikipedia.org/wiki/Parallel_slowdown) is an effect that can plague certain parallel tasks. Scaling the task beyond a certain amount of parallel nodes causes a runtime increase instead of the expected decrease. This is typically associated with a communications bottleneck, where the time required for communication between the parallelly executed parts grows faster than can be compensated by dividing the workload among the parallel nodes.

#### Compensated Amdahl's law

Whether parallel slowdown is caused by a communications bottleneck or not, it scales with the amount of available nodes. This overhead effect can be viewed as an additional non parallelizable part of the task. Furthermore, two modelling assumptions are made:

 - There is no overhead when only one node is available.
 - The overhead time scales linearly with the amount of parallel nodes.

The resulting speedup is thus:

$ T_{total} = T_{serial} + T_{parallel} $

$ Speedup(k) = \frac{T_{total}}{T_{serial} + (\frac{T_{parallel}}{k}) + ((k - 1) \times T_{overhead})} $

$ k $ := number of parallel nodes


##### Compensated example

Examining the previous example, but also taking an overhead of 1% (of $ T_{total} $) into account, results into the following relationship between available parallel nodes and maximum theoretical speedup.

![Amdahl Example](../image/compensated_amdahl.png){:width="900px"}

The maximum speedup of about 4.255 is achieved using 10 parallel nodes, a far cry from the maximum of 20 that the uncompensated Amdahl's law predicted. Using 150 nodes results in a speedup of about 0.65, which is actually a significant performance decrease. 