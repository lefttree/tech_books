# Detecting values in JS

Comparing a variable against only `null` doesn't give you enough information
about the value to determine whether it's safe to proceed.

## Detecting Primitive Values

Use `typeof`

5 primitive types:

- string
- number
- boolean
- null
- undefined

```javascript
if (typeof name === "string")
if (typeof count === "number")
if (typeof found === "boolean" && found)
if (typeof MyApp === "undefined")
```

if one of the expected values is actually `null`, just test `null` directly.

```javascript
if (element !== null)
```

## Detecting Reference Values

Reference values are also known as `objects`, so `typeof` always return `object`.

use `instanceof`.

```javascript
if (value instanceof Date)
if (value instanceof RegExp)
```

`instanceof` not only checks the constructor used to create teh object but also
checks the prototype chain.

It also works with custom types that you've defined for yourself. It's the only
good way to detect custom types. However, it doesn't work across frame.

```javascript
function Person(name) {
    this.name = name;
}
var me = new Person("Nicholas");

console.log(me instanceof Person); // true
```

## Detecting Functions

`typeof`, the `typeof` works with functions and also works across frames.

```javascript
if (typeof myFunc === "function")
```

Limitation: browser <= IE8. use `in` first to check if the function is defined
in `document`.

## Detecting Arrays

Best way

```javascript
function isArray(value) {
    return Object.prototype.toString.call(value) === "[object Array]";
}
```

A lot of libraries have implemented this. Since that time, ECMAScript 5 has
introducted `Array.isArray()` formally into Javascript.

So

```javascript
function isArray(value) {
    if (typeof Array.isArray === "function") {
        return Array.isArray(value);
    } else {
        return Object.prototype.toString.call(value) === "[object Array]";
    }
}
```

## Dectecting Properties

Use `in`

if only want to check for the existence of the property on the object instance,
use `hasOwnProperty()`.

```javascript
if ("hasOwnProperty" in object && object.hasOwnProperty(value))
```
