---
layout: post
title: "AS3 Speed Test: Array Vs Vector"
description: ""
category: "test" 
tags: ["actionscript3", "test", "array", "vector"]
---
{% include JB/setup %}

Since Flash Player 10 we have two options to work with containers: Array and Vector.<br>
Flash Array class is identical to JavaScript Array, they have the same interface.<br>
So, why a new container?<br>

Vector is a typed container where all elements are of the same class. In my view, somehow it's similar to C native vectors - and in Flash they are widely used for bitmaps, 3D, etc.<br>
According to [Vector's official documentation](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/Vector.html), there are a set of differences between both containers:<br>
> * A Vector is a dense array. (...)<br>
> * A Vector can optionally be fixed-length, (...)<br>
> * Access to a Vector's elements is bounds-checked. (...)<br>

Thus, the Vector would have some benefits over Array, which one of them is:<br>
> Performance: array element access and iteration are much faster when using a Vector instance than they are when using an Array.<br>
For a while I gave credit to Adobe's word, but I heard that Array is faster than Vector from different sources. Then, I got curious and decided to make a speed test (in fact it's a fight).<br>

Five operations are tested for both classes, running up to 10.000.000 iterations:
* push;
* access;
* pop;
* unshift; and
* shift.

In all computers the results were very similar, check the values above:<br>
1. __push__ (10.000.000 iterations)
  * Array: 659 ms<br>
  * Vector: 1337 ms<br>
  * Array was ~2 times faster<br>
2. __access__ (10.000.000 iterations)
  * Array: 48 ms<br>
  * Vector: 40 ms<br>
  * Vector was 1.2 times faster<br>
3. __pop__ (10.000.000 iterations)
  * Array: 223 ms<br>
  * Vector: 107 ms<br>
  * Vector was ~2.1 times faster<br>
4. __unshift__ (50.000 iterations)
  * Array: 778 ms<br>
  * Vector: 1569 ms<br>
  * Array was ~2 times faster<br>
5. __shift__ (50.000 iterations)
  * Array: 838 ms<br>
  * Vector: 1665 ms<br>
  * Array was ~2 times faster<br>

In conclusion, Array was faster than Vector - proving that operations over Vectors are not *much faster* than when using Array.<br>
Vist the [repository](https://github.com/loteixeira/VectorVsArray) where the test is hosted.<br>
Also, try running the [online version](http://disturbedcoder.com/files/VectorVsArray.swf).
