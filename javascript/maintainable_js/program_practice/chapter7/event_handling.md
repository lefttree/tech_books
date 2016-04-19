# Event Handling

Most event-handlingi code is very tightly coupled to the event environment and
therefore is not very maintainable.

## Classic Usage

```javascript
// Bad practice
function handleClick(event) {
    var popup = document.getElementById("popup");
    popup.style.left = event.clientX + "px";
    popup.style.top = event.clientY + "px";
    popup.className = "reveal";
}

addListener(element, "click", handleClick);
```

## Better Way

1. Separate Application Logic

It's always best to split application logic from any event handler, because the
same logic may need to be triggered by different actions in the future.

Another downside is for testing. It would be better to trigger the functionality
with a simple function call.

2. Don't Pass the Event Object Around

The `event` object has potentially dozens of additional pieces of information
about the event, the code might only use some of them.

Application logic should never rely on the event object to function properly.

- The method interface makes it unclear what pieces of data are actually necessary.
- need to recreate an `event` object in order to test the method.


```javascript
var MyApplication = {
    handleClick: function(event) {
        this.showPopup(event.clientX, event.clientY);
    }

    showPopup: function(x, y) {
        var popup = document.getElementById("popup");
        popup.style.left = x + "px";
        popup.style.top = y + "px";
        popup.className = "reveal";
    }
};

addListener(element, "click", function(event) {
    MyApplication.handleClick(event);
});


// Easy to test
MyApplication.showPopup(10, 10);
```
