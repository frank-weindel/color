# color
`color` is a JavaScript library for color conversion and manipulation with support for CSS color strings.

```javascript
var color = Color("#7743CE");

color.alpha(0.5).lighten(0.5);

console.log(color.hslString());  // "hsla(262, 59%, 81%, 0.5)"
```

## Install

### browser
Download the latest [color.js](https://github.com/harthur/color/tree/gh-pages). The `Color` object is exported.

### node
For [node](http://nodejs.org) with [npm](http://npmjs.org):

```bash
npm install color
```

And use with `var Color = require("color")`

## API

### Setters

```javascript
var color = Color("rgb(255, 255, 255)")
var color = Color({r: 255, g: 255, b: 255})
var color = Color().rgb(255, 255, 255)
var color = Color().rgb([255, 255, 255])
```
Pass any valid CSS color string into `Color()` or a hash of values. Also load in color values with `rgb()`, `hsl()`, `hsv()`, `hwb()`, and `cmyk()`.

```javascript
color.red(120)
```
Set the values for individual channels with `alpha`, `red`, `green`, `blue`, `hue`, `saturation` (hsl), `saturationv` (hsv), `lightness`, `whiteness`, `blackness`, `cyan`, `magenta`, `yellow`, `black`

### Getters


```javascript
color.rgb()       // {r: 255, g: 255, b: 255}
```
Get a hash of the rgb values with `rgb()`, similarly for `hsl()`, `hsv()`, and `cmyk()`

```javascript
color.rgbArray()  // [255, 255, 255]
```
Get an array of the values with `rgbArray()`, `hslArray()`, `hsvArray()`, and `cmykArray()`.

```javascript
color.red()       // 255
```
Get the value for an individual channel.

### CSS Strings

```javascript
color.hslString()  // "hsl(320, 50%, 100%)"
```

Different CSS String formats for the color are on `hexString`, `rgbString`, `percentString`, `hslString`, `hwbString`, and `keyword` (undefined if it's not a keyword color). `"rgba"` and `"hsla"` are used if the current alpha value of the color isn't `1`.

### Luminosity

```javascript
color.luminosity();  // 0.412
```
The [WCAG luminosity](http://www.w3.org/TR/WCAG20/#relativeluminancedef) of the color. 0 is black, 1 is white.

```javascript
color.contrast(Color("blue"))  // 12
```
The [WCAG contrast ratio](http://www.w3.org/TR/WCAG20/#contrast-ratiodef) to another color, from 1 (same color) to 21 (contrast b/w white and black).

```javascript
color.light();  // true
color.dark();   // false
```
Get whether the color is "light" or "dark", useful for deciding text color.

### Manipulation

```javascript
color.negate()         // rgb(0, 100, 255) -> rgb(255, 155, 0)

color.lighten(0.5)     // hsl(100, 50%, 50%) -> hsl(100, 50%, 75%)
color.darken(0.5)      // hsl(100, 50%, 50%) -> hsl(100, 50%, 25%)

color.saturate(0.5)    // hsl(100, 50%, 50%) -> hsl(100, 75%, 50%)
color.desaturate(0.5)  // hsl(100, 50%, 50%) -> hsl(100, 25%, 50%)
color.greyscale()      // #5CBF54 -> #969696

color.whiten(0.5)      // hwb(100, 50%, 50%) -> hwb(100, 75%, 50%)
color.blacken(0.5)     // hwb(100, 50%, 50%) -> hwb(100, 50%, 75%)

color.clearer(0.5)     // rgba(10, 10, 10, 0.8) -> rgba(10, 10, 10, 0.4)
color.opaquer(0.5)     // rgba(10, 10, 10, 0.8) -> rgba(10, 10, 10, 1.0)

color.rotate(180)      // hsl(60, 20%, 20%) -> hsl(240, 20%, 20%)
color.rotate(-90)      // hsl(60, 20%, 20%) -> hsl(330, 20%, 20%)

color.mix(Color("yellow"))        // cyan -> rgb(128, 255, 128)
color.mix(Color("yellow"), 0.3)   // cyan -> rgb(77, 255, 179)

// chaining
color.green(100).greyscale().lighten(0.6)
```

### Clone

You can can create a copy of an existing color object using `clone()`:

```javascript
color.clone() // -> New color object
```

And more to come...

## Propers

The API was inspired by [color-js](https://github.com/brehaut/color-js). Manipulation functions by CSS tools like Sass, LESS, and Stylus.
