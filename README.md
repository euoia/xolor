`xcolor`
====================

Description
-----------
An extensive color manipulation library.

Calculating Colors
---
```javascript
// Calculate a grey level color value
xolor('#c00').greyfilter()

// Calculate a gradient color between #fc0 and #f00 23% of the way through the gradient
xolor('#fc0').gradientlevel('#f00', .23)

// Calculate the visible color when lightgrey is overlayed on top of #f00 with an opacity of 69%.
xolor('#f00').opacity('lightgrey', 0.69)
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

License
======
Dual licensed under the MIT or GPL Version 2 licenses.
