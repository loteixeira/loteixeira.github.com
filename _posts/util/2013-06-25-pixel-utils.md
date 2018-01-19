---
layout: post
title: "AS3 Pixel Conversion Utils"
categories: util
---

Flash programmers are not used to bitwise operations. Period.

Even though, such operations are indeed very important in ActionScript3. For example, pixel components (red, green, blue and alpha) are commonly packed into a 32 bits unsigned integer - see [BitmapData's official documentation](http://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/flash/display/BitmapData.html).

To lend you a hand, I created a simple static class (Pixel class) which provides ways to convert pixels stored in uints to higher level structures like Arrays/Objects and vice versa.

Usage:<br>

	var sourceArray:Array; // source pixel as an array
	var sourceObj:Object;  // source pixel as an object
	var sourcePixel:uint;  // source pixel as an unsigned integer

	// 24 bits pixel conversion - RGB format
	var uintFromArray:uint = Pixel.arr2int(sourceArray);
	var uintFromObject:uint = Pixel.obj2int(sourceObj);
	var arrayFromUint:Array = Pixel.int2arr(sourcePixel);
	var objectFromUint:Object = Pixel.int2obj(sourcePixel);

	// 32 bits pixel conversion - ARGB format
	var uintFromArray32:uint = Pixel.arr2int32(sourceArray);
	var uintFromObject32:uint = Pixel.obj2int32(sourceObj);
	var arrayFromUint32:Array = Pixel.int2arr32(sourcePixel);
	var objectFromUint32:Object = Pixel.int2obj32(sourcePixel);

	// 24 bits examples
	var result1:uint = Pixel.arr2int([0xff, 0xcc, 0x88]);
	var result2:uint = Pixel.obj2int({r: 150, g: 100, b: 50});
	var result3:Array = Pixel.int2arr(0xff00ff);
	var result4:Object = Pixel.int2obj(0x00ffcc);

	// 32 bits examples
	var result5:uint = Pixel.arr2int32([0xff, 0xff, 0xcc, 0x88]);
	var result6:uint = Pixel.obj2int32({a: 80, r: 150, g: 100, b: 50});
	var result7:Array = Pixel.int2arr32(0xffff00ff);
	var result8:Object = Pixel.int2obj32(0xbb00ffcc);

The requeriments of using Arrays as source pixels are at least 3 elements for 24 bits and at least 4 elements for 32 bits.
And for Objects the members 'r', 'g' and 'b' must exist for 24 bits and 'a', 'r', 'g' and 'b' must exist for 32 bits.

Check Pixel class gist [here](https://gist.github.com/loteixeira/5637721).