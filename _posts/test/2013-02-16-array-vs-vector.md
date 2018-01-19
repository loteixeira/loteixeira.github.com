---
layout: post
title: "AS3 Speed Test: Array Vs Vector"
date: 2013-02-16
category: "test" 
---

Since Flash Player 10 we have two options to work with containers: Array and Vector.<br>
Flash Array is identical to JavaScript Array, they have the same interface.<br>
And about Vector?<br>

Vector is a typed container where all elements are of the same class. In my view it's similar to C native vectors - even because in Flash they are widely used for bitmaps, 3D, etc.<br>
According to [Vector's official documentation](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/Vector.html), there are a set of differences between both containers:<br>
> * A Vector is a dense array. (...)<br>
> * A Vector can optionally be fixed-length, (...)<br>
> * Access to a Vector's elements is bounds-checked. (...)<br>

Thus, a Vector would have some benefits over an Array, which one of them is:<br>
> Performance: array element access and iteration are much faster when using a Vector instance than they are when using an Array.<br>
For a while I gave credit to Adobe's word, but I heard from different sources that Array is faster than Vector. Then I made a speed test to take my own conclusions.<br>

Five operations with integers were tested for both classes:
* push;
* access;
* pop;
* unshift; and
* shift.

Check the average time values below (the test ran five times):<br>

	push (10.000.000 iterations):
	* Array: 603,6 ms
	* Vector: 1120,6 ms
	Array was ~1,856 times faster

	access operator[] (10.000.000 iterations):
	* Array: 48,8 ms
	* Vector: 40 ms
	Vector was 1,22 times faster

	pop (10.000.000 iterations):
	* Array: 221,8 ms
	* Vector: 102,8 ms
	Vector was ~2,157 times faster

	unshift (50.000 iterations):
	* Array: 784,4 ms
	* Vector: 779,6 ms
	Vector was ~1,006 times faster

	shift (50.000 iterations):
	* Array: 833,2 ms
	* Vector: 833 ms
	The values may be considered equivalent

In conclusion, maybe it's not safe to say that operations with Vectors are _much faster_ than operations with Arrays. The time difference between Array.push and Vector.push, for example, makes Array more likely when you need to add dinamically elements into the end of the container. And the other operations don't seems to have a big speed boost with Vectors.<br>
Vist the [source code repository of the test](https://github.com/loteixeira/VectorVsArray) and [run the online version](http://disturbedcoder.com/files/VectorVsArray.swf).<br>

Computer specification:
* Processor: Intel Core 2 Duo @ 2.80 GHz
* RAM: 4 GB
* OS: Windows 7 64-bit
* Flash Player: Version 11.6.602.167