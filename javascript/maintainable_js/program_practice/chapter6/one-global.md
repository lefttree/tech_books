# The One-Global Approach

By agreeing to create only one global object.

The idea behind the one-global approach is to create a single global with a
unique name and the attach all your functionality onto that one global. Just like
jQuery or $.

## Namespaces

It is possible to start polluting your one global as well.

Example YUI

- `Y.DOM`
- `Y.Event`
- `Y.My` : My Yahoo!
- `Y.Mail` : Mail

A common convertion is for each file to declare its own namespace by creating a
new object on the global.

There are also times when each file is simply adding to a namespace; in this
case, you may want a little more assurance that the namespace already exists.

```javascript
var YouGlobal = {
    namespace: function(ns) {
        var parts = ns.spilt("."),
            object = this,
            i, len;

        for (i=0, len=parts.length; i < len; i++) {
            if (!object[parts[i]]) {
                object[parts[i]] = {};
            }
            object = object[parts[i]];
        }
        return object;
    }
}

// Usage
YouGlobal.namespace("Books.MaintainableJavascript");
YouGlobal.Books.MaintainableJavascript.author = "Nicholas C. Zakas";
```

## Modules

No module syntax before(ECMAScript 6)

1. YUI modules
2. AMD modules
3. RequireJS
