# Loose Coupling

## What is loose coupling

Able to make changes to a single component without making changes to other components

It's easy to maintain and debug.

## Keep JS out of CSS

CSS expressions: avoid it

## Keep CSS out of JS

When JS needs to change the style of an element, the best way to do so is by
**manipulating CSS classes**.

Example: to reveal a dialog box on the page

```css
.reveal {
    color: red;
    left: 10px;
    top: 100px;
    visibility: visible;
}
```

Then in JS, add the class to the element

```javascript
// Native
element.className += " reveal";
// HTML5
element.classList.add("reveal");
// jQuery
$(element).addClass("reveal");
```

> There is one instance in which use `style` is acceptable: position

## Keep JS out of HTML

Bad

```html
<button onclick="doSomething()" id="action-btn">click</button>
```

**Recommendded style**

- Use javascript to add eventlistener
- Don't use in-line JS

## Keep HTML out of JS

`innerHTML`
