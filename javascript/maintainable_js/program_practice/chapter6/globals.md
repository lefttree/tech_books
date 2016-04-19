# Avoid Globals

The JS execution env is unique in a lot of ways. One of those ways is in the use
of global veriables and functions.

In browsers, the `window` object is typically overloaded to also be the global
object, so any variable or function declared in the global scope becomes a
property of the window object.

## The Problems with Globals

### Naming Collisions

### Code Fragility

A function that depends on globals is tightly coupled to the environment. If the
environment changes, the function is likely to break.

**When defining functions, it's best to have as much data as possible local to the
function.**

Any data that comes from outside the function should be passed in as an argument.

### Difficulty Testing

Any function taht relies on global variables to work requires you to recreate the
entire global environment to properly test that function.

Have to maintain 2 global environments: production and testing.

## Accidental Globals

When you assign a value to a variable that has not previously been defined in a
`var` statement, JS auto creates a global variable.

### Avoiding Accidental Globals

1. JSLint and JSHint
2. use strict mode


