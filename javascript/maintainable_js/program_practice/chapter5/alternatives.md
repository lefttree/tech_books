# Alternatives

ALternatives to manipulate HTML in JS.

## Load from the server

The first is to keep the templates remote and use `XMLHttpRequest` to retrieve
additional markup. This approach is more convenient for single-page applications
than for multiple-page applications.

It's useful when you need to inject a large amount of HTML into the page. For
performance reasons, it's typically not a good idea to keep large amounts of
unused markup in memory or in the DOM. For smaller markup chunks, you may want
to consider client-side templates.

```javascript
function loadDialog(name, oncomplete) {
    var xhr = new XMLHttpRequest();
    xhr.open("get", "/js/dialog/" + name, true);

    xhr.onreadystatechange = function() {
        if (xhr.readyState == 4 && xhr.status == 200) {
            var div = document.getElementById("dlg-holder");
            div.innerHTML = xhr.responseText; // load html
            oncomplete();
        } else {
            // handle error
        }
    }
}
```

Use jQuery

```javascript
function loadDialog(name, oncomplete) {
    $("#dlg-holder").load("/js/dialog/" + name, oncomplete);
}
```

## Simple Client-Side Templates

client side templates are markup pieces with slots that must be filled by JS in
order to be complete.

Example

```javascript
var templateText = "<li><a href="%s">%s</a></li>";

function sprintf(text) {
    var i = 1, args = arguments;
    return text.replace(/%s/g, function() {
        return (i < args.length) ? args[i++] : "";
    });
}

// usage
var result = sprintf(templateText, "/item/4", "Fourth item");
```

### Getting template text into JS

1. include the template as an HTML comment
2. embed the templates into an HTML page by using a `<script>` element with a
custom `type` property

## Complex Client-Side Templates

[Handlebars](http://handlebarsjs.com)

1. It suggests `<script>` way to embed template in an HTML page
2. also allow you to put simple logic and looping into the templates
