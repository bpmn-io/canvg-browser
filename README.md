# canvg-browser

[![Build Status](https://travis-ci.com/bpmn-io/canvg-browser.svg?branch=master)](https://travis-ci.com/bpmn-io/canvg-browser)

A port of [canvg](https://github.com/gabelerner/canvg) that properly works in the browser as CommonJS module.


## Differences to [canvg](https://github.com/gabelerner/canvg)

* Exposes CommonJS module
* Dependencies such as `rgbcolor` and `stackblur` are required in the CommonJS way, too
* Test cases verify this project works in the browser


## Installation
`npm install canvg-browser --save`


## Usage
Put a canvas on your page:

```html
<canvas id="canvas" width="200px" height="200px"></canvas>
```

```js
var canvg = require('canvg-browser'),
    canvas = document.getElementById('canvas');

var svg = '<svg height="100" width="100"><circle cx="50" cy="50" r="40" stroke="black" /></svg>';

var options = {
  log: false,
  ignoreMouse: true
};

canvg(canvas, svg, options);
```


### Options

* log: true => console.log information
* ignoreMouse: true => ignore mouse events
* ignoreAnimation: true => ignore animations
* ignoreDimensions: true => does not try to resize canvas
* ignoreClear: true => does not clear canvas
* offsetX: int => draws at a x offset
* offsetY: int => draws at a y offset
* scaleWidth: int => scales horizontally to width
* scaleHeight: int => scales vertically to height
* renderCallback: function => will call the function after the first render is completed
* forceRedraw: function => will call the function on every frame, if it returns true, will redraw
* useCORS: true => will attempt to use CORS on images to not taint canvas

You can call canvg without parameters to replace all svg images on a page. See the [example](http://gabelerner.github.io/canvg/examples/convert.htm).

There is also a built in extension method to the canvas context to draw svgs similar to the way [drawImage](http://www.w3.org/TR/2dcontext/#dom-context-2d-drawimage) works:
```javascript
var c = document.getElementById('canvas');
var ctx = c.getContext('2d');
ctx.drawSvg(SVG_XML_OR_PATH_TO_SVG, dx, dy, dw, dh);
```


### Related Repositories
* [canvg](https://github.com/gabelerner/canvg)
