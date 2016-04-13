# Variable

## Variable Declaration

All `var` statements are **hoisted** to the top of the containing function
regardless of where they actually occur in the code.

All **declaration** are hoisted.

**Recommended Style**

- have all variables declared at the top of a function instead of scattered throughout.
- combine `var` statements

```javascript
function doSomething(items) {
    var value = 10,
        result = value + 10,
        i,
        len;

    for (i=0, len=items.length; i < len; i++) {
        do(items[i]);
    }
}
```
