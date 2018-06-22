---
layout: default
title: "Floating point"
--- 

#### Floating point data

Floating point (FP) data is a common way to store real numbers [(R)](https://en.wikipedia.org/wiki/Real_number). Many different types of floating point datatypes exist, but the most relevent types for scientific computing are:

 - Double (FP64)
 - Single (FP32)
 - Half (FP16)

[**Double** (64 bit)](https://en.wikipedia.org/wiki/Double-precision_floating-point_format):

Common format for sensitive mathematical equations, like solving ill conditioned systems. Default datatype of MATLAB.

$$ Value = -Sign_{2} \times 2^{(Exponent_{2} - 1023)} \times (1 + Mantissa_{2}) $$

 - 1 bit: sign
 - 11 bit: exponent
 - 53 bit: mantissa

Resolution: $$ (1/2)^{52} = 2.2204e-16 $$

Exponent range: $$ 2^{([-1023,1024])} $$

[**Single** (32 bit)](https://en.wikipedia.org/wiki/Single-precision_floating-point_format):

Original floating point datatype used in 32 bit computers, provides sufficient resolution for many mathematical operations.

$$ Value = -Sign_{2} \times 2^{(Exponent_{2} - 127)} \times (1 + Mantissa_{2}) $$

 - 1 bit: sign
 - 8 bit: exponent
 - 23 bit: mantissa

Resolution: $$ (1/2)^{23} = 1.1921e-07 $$

Exponent range: $$ 2^{([-127,128])} $$

[**Half** (16 bit)](https://en.wikipedia.org/wiki/Half-precision_floating-point_format):

Relatively coarse approximation of a real number, but sometimes good enough. A great example of aplications that usually don't require more precision are  deep neural networks.

$$ Value = -Sign_{2} \times 2^{(Exponent_{2} - 15)} \times (1 + Mantissa_{2}) $$

 - 1 bit: sign
 - 5 bit: exponent
 - 10 bit: mantissa

Resolution: $$ (1/2)^{52} = 9.7656e-04 $$

Exponent range: $$ 2^{([-15,16])} $$