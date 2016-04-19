# The Zero-GLobal Approach

This approach is quite limited, so it's useful only in some very specific situations.

The most common situation is with a completely standalone script that doesn't
have to be accessed by any other scripts.

```javascript
(function(win){
    "use strict";

    var doc = win.document;

    // declare other variables here

    // other code goes here
}(window));
```
