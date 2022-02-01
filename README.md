### Public Link: https://sssoltannn.github.io/inspect-blocker

<hr>

## Tutorial

Create .js file for block inspect functions (blockInspect.js) and connect that to your HTML file.

```
<script src="<path of js file>"></script>
```

<hr>

### Step 1

Use of F12 key on the browser.

<strong>blockInspect.js</strong>

```
$(document).keydown(function(e){
    if(e.which === 123){
       return false;
    }
});
```

<hr>

### Step 2

Use of Right click. In this step, you have 2 way to do that.

- Method 1

<strong>index.html</strong>

```
<html oncontextmenu="return false">
</html>
```

- Method 2

<strong>blockInspect.js</strong>

```
$(document).bind("contextmenu",function(e) {
	e.preventDefault();
});
```

<hr>

### Step 3

Use of other shortcuts involving Ctrl keys.

<strong>Note:</strong> It will affect another Ctrl shortcuts too.

- Ctrl +

  - R (Refresh)
  - C (Copy)
  - P (Paste)
  - T (New Tab)
  - S (Save)

    and all another Ctrl shortcuts will be disabled.

<strong>index.html</strong>

```
<body oncontextmenu="return false" onkeydown="return false;" onmousedown="return false;">
</body>
```

<hr>

### Step 4

By temporarily removing DOM when inspector is opened.

<strong>blockInspect.js</strong>

```
var currentHtmlContent;

var element = new Image();

var elementWithHiddenContent = document.querySelector("#element-to-hide");

var innerHtml = elementWithHiddenContent.innerHTML;

element.__defineGetter__("id", function() {
    currentHtmlContent= "";
});

setInterval(function() {
    currentHtmlContent= innerHtml;
    console.log(element);
    console.clear();
    elementWithHiddenContent.innerHTML = currentHtmlContent;
}, 1000);
```

<hr>
