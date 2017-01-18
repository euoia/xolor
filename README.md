`xcolor`
====================
**Automatically beautiful**

An extensive color manipulation library for the browser and node.js. While extensive, this library is less than 6KB in size (minified and gzipped).

Calculating Colors
---
```javascript

var c = xolor('#c00')

// Calculate a grey level color value
c.greyfilter()

// Calculate a gradient color between #fc0 and #f00 23% of the way through the gradient
c.gradient('#f00', .23)

// Calculate the visible color when lightgrey is overlayed on top of #f00 with an opacity of 69%.
c.opacity('lightgrey', .69)

// Return a color that's 10% lighter
c.lightness(1.1 * c.lightness())

// Chain them together
c.subtractive('#2a3e37').lighter(.1).triad()

```

Colorizing Text
----
```javascript
var element = document.getElementById('foo')
xolor.colorize(element, "burntsienna", "blue", function() {
   // Colors each character a random color between "burntsienna" and "blue"
   return Math.random()
})
```

Further examples
==========================
This library was ported from the [jquery xcolor plugin](https://github.com/infusion/jQuery-xcolor), and has all the non-jQuery related functionality that library had.
Some great documentation for that library that will help understand the methods in this library, see the code examples and demonstrations here: http://www.xarg.org/project/jquery-color-plugin-xcolor/

Install
=======

```
npm install xolor
```

Usage
=====

Accessing xolor:
```javascript
// node.js
var xolor = require('xolor')

// amd
require.config({paths: {xolor: '../dist/xolor.umd.js'}})
require(['xolor'], function(xolor) { /* your code */ })

// global variable
<script src="xolor.umd.js"></script>
xolor; // xolor.umd.js can define xolor globally if you really
          //   want to shun module-based design
```

Using xolor:

**`xolor(cssColorString)`** - Constructor. Takes in either a css color like `"lightskyblue"`, `"#fff"`, `"#fff000"`, `"rgb(1, 234, 56)"`, `"rgb(66%, 55%, 44%)"`,  
**`xolor(rgbObject)`** - an rgb object like `{r:34,g:45,b:56}`,  
**`xolor(rgbString)`** - a comma-sparated rgb string like `"34,45,56"`,  
**`xolor(rgbArray)`** - an array where each element is interpreted as an rgba component [r,g,b,a] like `[34,45,56]`,  
**`xolor(hslColorString)`** - an [hsl/hsb](https://en.wikipedia.org/wiki/HSL_and_HSV) color like `"hsl(10, 90, 20)"` or `"hsb(10, 90, 20)"`  
**`xolor(hslObject)`** - an hsl object like `{h:10,s:90,l:20}` or `{h:10,s:90,b:20}`,  
**`xolor(hsvColorString)`** - an [hsv](https://en.wikipedia.org/wiki/HSL_and_HSV) color like `"hsv(64, 40, 16)"`  
**`xolor(hslObject)`** - an hsv object like `{h:64,s:40,v:16}`,  
**`xolor(integer)`** - an integer where the least significant 2 bytes represent blue, the next 2 bytes represent green, the next 2 represent red, and the most significant bytes represent alpha.

**`xolor(xolorObject)`** - Returns a copy of the passed in xolor object.

**`xolor.random()`** - Returns a xolor object representing a random color with 100% opacity.

**`xolor.readable(background, textColor, fontSize)`** - Returns true if text will be readable at the given size with the given background and text colors.  
**`xolor.readable(domNode)`**
* `background` - The background color. *Can be any value the `xolor` constructor can take in.*
* `textcolor` - The text color. *Can be any value the `xolor` constructor can take in.*
* `fontSize` - The font size in pixels. Default: 10.
* `domNode` - A domNode to check for readability.

**`xolor.colorize(domNode, from, to, methodFn)`** - Colors the text within a domNode.  
**`xolor.colorize(domNode, from, to, methodString)`**
* `domNode` - The domNode to color.
* `from` - The color the first letter should be.
* `to` - The color the last letter should be.
* `methodFn(charsProcessed,textLength,lastPosition,character)` - The method used to transition between `from` and `to`. Is a function that should return a number between 0 and 1 indicating how far from `from` and how close to `to` the color will be at the given position.
  * `charsProcessed` - The number of characters tha have been processed (ie the index of the character).
  * `textLength` - The full length of text in this node.
  * `lastPosition` - The last position returned by a call to this method. Starts at 0.
  * `character` - The character at the given position.
* `methodString` - The method used to transition between `from` and `to`. Can be one of the following values:
  * `"gradient"` - A smooth gradient between `from` and `to`.
  * `"flip"` - Flips between `from` and `to` every visible character.
  * `"pillow"` - A smooth gradient between `from` and `to` and back to `from`.

####Instance methods and properties:

**`xolorObject.r`** - Returns the red part of the xolor. Setting this value mutates the color.  
**`xolorObject.g`** - Returns the green part of the xolor. Setting this value mutates the color.  
**`xolorObject.b`** - Returns the blue part of the xolor. Setting this value mutates the color.  
**`xolorObject.a`** - Returns the alpha part of the xolor. Setting this value mutates the color.  
**`xolorObject.rbg`** - Returns an rbga object representing the color (like `{r:34,g:45,b:56,a:1}`).  
**`xolorObject.css`** - Returns a css color string representing the color (either `"transparent"` or a css rbg or rbga string like `"rgb(1, 234, 56)"`).  
**`xolorObject.fraction`** - Returns an rbga object where each property is a number from 0 to 1 representing a percentage of full color. To clarify, `xolor('rbg(10%,20%,30%)').fraction` would return `[0.1, 0.2, 0.3]`.  
**`xolorObject.array`** - Returns an array where each element represents an rgba value. To clarify, `xolor('rbg(20,50,100)').array` would return `[20,50,100]`.  
**`xolorObject.hsl`** - Returns an [hsla](https://en.wikipedia.org/wiki/HSL_and_HSV) object representing the color in Hue-Saturation-Lightness format.  
**`xolorObject.hsv`** - Returns an [hsva](https://en.wikipedia.org/wiki/HSL_and_HSV) object representing the color in Hue-Saturation-Value format.  
**`xolorObject.hex`** - Returns a hex string value representing the color.  
**`xolorObject.toString()`** - Same as `xolorObject.hex`.  
**`xolorObject.int`** - Returns an integer where the least significant 2 bytes represent blue, the next 2 bytes represent green, the next 2 represent red, and the most significant bytes represent alpha.  
**`xolorObject.name`** - Returns the closest name for the color from this list: http://www.w3.org/TR/css3-color/#svg-color 

**Combinations two colors:**

Each of these functions returns a new xolor object based on a function of two colors. 
Xolor objects are never mutated by commands on them - all methods return new objects and are, consequently, chainable.

**`xolorObject.blend(topColor, opacity)`** - Returns the color that would show if `topColor` was over the `xolorObject`'s color with the given `opacity`.  
**`xolorObject.combine(otherColor)`** - Returns the two colors combined with a ximple XOR method.  
**`xolorObject.breed(otherColor)`** - Returns a xolor with random parts of each color.  
**`xolorObject.add(otherColor)`** - Returns the [additive mix](https://en.wikipedia.org/wiki/Additive_color) of the two colors.  
**`xolorObject.subtractive(otherColor)`** - Returns the [subtractive mix](https://en.wikipedia.org/wiki/Subtractive_color) of the two colors.  
**`xolorObject.subtract(otherColor)`** - Returns the subtraction of the two colors. I don't believe this is a standard color method.  
**`xolorObject.mult(otherColor)`** - Returns the multiplicative mix of the two colors.  
**`xolorObject.multiply(otherColor)`** - Alias for `mult`.  
**`xolorObject.avg(otherColor)`** - Returns a color between the two colors by averaging the rgb parts.  
**`xolorObject.average(otherColor)`** - Alias for `avg`.  
**`xolorObject.gradient(otherColor, position)`** - Returns the color on a gradient between the two colors at the given `position` on the gradient.
* `otherColor` - Can be any value the `xolor` constructor can take in.
* `position` - A number from 0 to 1 representing how close to `otherColor` the returned color should be (where 1 represents the `otherColor` exactly).

**Related colors:**

The following methods return a single xolor object:

**`xolorObject.inverse()`** - Returns the inverse xolor.  
**`xolorObject.web()`** - Returns a ["web safe"](https://en.wikipedia.org/wiki/Web_colors) xolor.  
**`xolorObject.complementary()`** - Returns of the [complementary color](https://en.wikipedia.org/wiki/Complementary_colors) as a a xolor object.  
**`xolorObject.comp()`** - Alias for `complementary`.  

**`xolorObject.red()`** - Returns a xolor with just the red part.  
**`xolorObject.green()`** - Returns a xolor with just the green part.  
**`xolorObject.blue()`** - Returns a xolor with just the blue part.  

**Color Attributes:**  
These methods return a color attribute when called with no argument, and return a new `xolor` object with that attribute modified if you do pass an argument.

**`xolorObject.lightness()`** - Returns the lightness level (a number between 0 and 255).  
**`xolorObject.lightness(level)`** - Returns a xolor with the lightness changed to the given `level` (a number between 0 and 255).  
**`xolorObject.hue()`** - Returns the hue (a number between 0 and 360).  
**`xolorObject.hue(newHue)`** - Returns a xolor with the hue changed to the passed `newHue` (a number between 0 and 360).  
**`xolorObject.saturation()`** - Returns the saturation as caluated in the HSV model (a number between 0 and 1).  
**`xolorObject.saturation(newSaturation)`** - Returns a xolor with the hue (*as caluated in the HSV model*) changed to the passed `newSaturation` (a number between 0 and 1).  
**`xolorObject.brightness()`** - Returns the brightness (aka "value") as caluated in the HSV model (a number between 0 and 1).  
**`xolorObject.brightness(newValue)`** - Returns a xolor with the brightness (aka "value", *as caluated in the HSV model*) changed to the passed `newValue` (a number between 0 and 1).  

**`xolorObject.luminosity()`** - Returns the [WCAG luminosity](https://www.w3.org/TR/WCAG20/#relativeluminancedef) (a number between 0 and 1).  

**Filters**:  
**`xolorObject.sepia()`** - Returns a xolor filtered by [microsoft's sepia filter](http://msdn.microsoft.com/en-us/magazine/cc163866.aspx).  
**`xolorObject.greyfilter(method)`** - Returns a grey version of the xolor.
* `method` - *(Default: 1)* Can be:
   * `1` - Robert Eisele's grey filter method
   * `2` - Sun's grey filter method
   * `3` - An unknown grey filter method (I'm not sure where it came from)

The following methods return arrays of xolor objects.

**`xolorObject.triad()`** - Returns the color's [triad](https://en.wikipedia.org/wiki/Color_scheme#Triadic_colors).  
**`xolorObject.tetrad()`** - Returns the color's [tetrad](https://en.wikipedia.org/wiki/Color_scheme#Tetradic_colors).  
**`xolorObject.splitcomplement()`** - Returns the color's [split complement](https://en.wikipedia.org/wiki/Color_scheme#Split-Complementary) colors.  
**`xolorObject.splitcomp()`** - Alias for `splitcomplement`.  
**`xolorObject.monochromatic(number)`** - Returns an array of [monochromatic colors](https://en.wikipedia.org/wiki/Monochromatic_color).  
**`xolorObject.monochromes(number)`** - Alias for `monochromatic`.  
**`xolorObject.analogous(number, slices)`** - Returns an array of [analogous color](https://en.wikipedia.org/wiki/Analogous_colors).
* `number` - *(Default:8)* The number of colors to return.
* `slices` - *(Default:32)* I'm not entirely sure what this parameter is.

**`xolorObject.schemeFromDegrees(hueDegreesArray)`** - Returns an array of xolor objects the same length as the array passed in. For example, `xolor('red').schemeFromDegrees([0, 120, 240])` is a triadic color scheme.
* `hueDegreesArray` - An array where each element is a number of degrees representing a color with a hue (0-360) that many degrees from the original color.

**Miscellaneous:**

**`xolorObject.distance(fromColor)`** - Returns an integer representing the "distance" between the `xolorObject`'s color and the `fromColor` color. `fromColor` can be any value you can pass into the `xolor` constructor (a number between 0 and 441.67). See [here](http://www.compuphase.com/cmetric.htm) for details.  
**`xolorObject.contrast(color2)`** - Returns the [WCAG contrast](https://www.w3.org/TR/WCAG20/#contrast-ratiodef) between the two colors (a number between 1 and 21).

How to Contribute!
============

Anything helps:

* Creating issues (aka tickets/bugs/etc). Please feel free to use issues to report bugs, request features, and discuss changes
* Updating the documentation: ie this readme file. Be bold! Help create amazing documentation!
* Submitting pull requests.

How to submit pull requests:

1. Please create an issue and get my input before spending too much time creating a feature. Work with me to ensure your feature or addition is optimal and fits with the purpose of the project.
2. Fork the repository
3. clone your forked repo onto your machine and run `npm install` at its root
4. If you're gonna work on multiple separate things, its best to create a separate branch for each of them
5. edit!
6. If it's a code change, please add to the unit tests (at test/xolor.js) to verify that your change
7. When you're done, run the unit tests and ensure they all pass
8. Commit and push your changes
9. Submit a pull request: https://help.github.com/articles/creating-a-pull-request

Change Log
=========

* 1.2.0
	* Adding hue, saturation, brightness, luminosity, schemeFromDegrees, and contrast
	* Removing relLightness and lighter
	* Changing `opacity` to `blend`
* 1.1.8 - Fixing colorize and adding full documentation
* 1.1.0 - Changed lightness and relLightness from getter/setters to functions
* 1.0.0 - Created based on https://github.com/infusion/jQuery-xcolor

Todo
=====

* documentation
* Incorporate more color methods from less.js
  * http://lesscss.org/functions/#color-channel
  * http://lesscss.org/functions/#color-operations
  * http://lesscss.org/functions/#color-blending
* Incorporate color methods from the "other useful javascript color modules"
* Incorporate missing methods listed here: http://stackoverflow.com/questions/10266123/hex-rgb-color-manipulation-methods/10266506#10266506
* Write tests
* Add HSI support
* Add HWB support
  * Add 'whiteness' and 'blackness' methods
* Add CMYK support

Thanks
========

Thanks goes out to:
* Robert Eisele who's [xColor jQuery plugin](https://github.com/infusion/jQuery-xcolor) is where I got much of the code for this module.

License
=======
Dual licensed under the [MIT](http://opensource.org/licenses/MIT) or GPL Version 2 licenses.

Other useful javacript color modules
=======

These modules may have manipulation methods not contained in this library:

* https://github.com/brehaut/color-js
* https://github.com/mbjordan/Colors
* https://github.com/gka/chroma.js

These modules have manipulations that are already contained in this xolor library as of last checking:
* https://github.com/Qix-/color