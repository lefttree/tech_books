# Function

## Function Declaration

Also hoisted by the Javascript engine.

**Recommendde Style**

- always be declared before being used.
- should never appear inside of block statements.

## Immediate Function Invocation

```javascript
var value = (function() {
    // function body

    return {
        message: "Hi"
    }
}());
```
