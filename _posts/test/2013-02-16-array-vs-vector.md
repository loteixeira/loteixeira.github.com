---
layout: post
title: "AS3 Speed Test: Array Vs Vector"
description: ""
category: "test" 
tags: ["actionscript3", "test", "array", "vector"]
---
{% include JB/setup %}

Since Flash Player 10 we have two options to work with containers: Array and Vector.<br>
Flash Array class is identical to JavaScript Array, the same interface and (almost) the same behavior.<br>
So, why a new container?<br>
In [Vector documentation page](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/Vector.html) Adobe says that it's faster than Array:<br>
> Performance: array element access and iteration are much faster when using a Vector instance than they are when using an Array.<br>
Oh really?<br>

For a while I gave some credit to Adobe's words, but one day a workmate told me that Array is faster than Vector. I got really curious.<br>

Thus, I decided to make a test (in fact it's a boxe fight) to check how much time each class takes to execute basic container operations.<br>

Five operations are tested for both classes:
* push;
* access;
* pop;
* unshift; and
* shift.

You may run the test and take your own conclusions.<br>
Visit the repo, where the test is hosted: [https://github.com/loteixeira/VectorVsArray](https://github.com/loteixeira/VectorVsArray)<br>
Also, you may check the online version of the test: [http://disturbedcoder.com/files/VectorVsArray.swf](http://disturbedcoder.com/files/VectorVsArray.swf)<br>

**MY CONCLUSION:<br>In every computer which I ran the test, Array is faster in mostly of operations.**<br>