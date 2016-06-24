# Doing the Unstuck: How to make browsers compatible with Web JavaScript™, *Mike Taylor, Mozilla*

## [@miketaylr](https://twitter.com/miketaylr)<br>[miket@mozilla.com](miket@mozilla.com)
### [webcompat.com](https://webcompat.com/)

[Arkansa’s state drink is *gravy*](https://en.wikipedia.org/wiki/List_of_U.S._state_beverages#Table)

### JavaScript

Mootools didn’t expect `String.prototype.contains`, so webpages broke. This is why we have `String.prototype.includes`.

`Array.prototype.contains()`

In ES6 added `Array.prototype.contains()` which is nonenemurable by default so Mootools code explodes

And that’s how we got `Array.prototype.includes()`

`Array.prototype.values()`

This broke Mootools, surprise! Broke JSFiddle which was using Mootools.

Solved with `Array.prototype[@@unscopables]`

### DOM

“This website does not support landscape view. Please turn your phone vertically to continue...”

`window.orientation`, Apple proprietary thing from iPhone 4 which was great but Apple sometimes forgets to write standards...

`undefined != 0` => `true`, call `badOrientation()`

Wrote the specs and reverse engineered `window.orientation`.

### CSSOM *(CSS Object Model)*

```
elm.style.webkitTransform       <= Works in chrome, firefox, safari, edge
elm.style.webkitTransform       <= also in spec
elm.style['-webkit-transform']
elm.style['transform']          <=
```

Sites developed only using `-webkit` prefixes wind up being broken in other browsers.

Apple forgot to write a spec so he did. `-webkit-background-clip: text;` now implemented in Gecko

### read standards *(and like, use web standards?)*

### use pre-release channels
