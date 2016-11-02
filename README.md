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

Install
=======

```
npm install xolor
```

Usage
=====

Accessing keysight:
```javascript
// node.js
var xolor = require('xolor')

// amd
require.config({paths: {xolor: '../dist/xolor.umd.js'}})
require(['xolor'], function(xolor) { /* your code */ })

// global variable
<script src="xolor.umd.js"></script>
xolor; // xolor.umd.js can define keysight globally if you really
          //   want to shun module-based design
```

Using xolor:

Full usage docs on their way..


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
6. If it's a code change, please add to the unit tests (at test/odiffTest.js) to verify that your change
7. When you're done, run the unit tests and ensure they all pass
8. Commit and push your changes
9. Submit a pull request: https://help.github.com/articles/creating-a-pull-request

Change Log
=========

* 1.0.0 - Created based on https://github.com/infusion/jQuery-xcolor

Thanks
========

Thanks goes out to dmauro who's [Keypress module](https://github.com/dmauro/Keypress) is where I got most of the keymapping information from.

License
=======
Dual licensed under the [MIT](http://opensource.org/licenses/MIT) or GPL Version 2 licenses.
