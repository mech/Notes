# Tips

```
// querySelectorAll return a NodeList, an array-like list
var nodes = document.querySelectorAll('a');

// In order to iterate it, we cannot use forEach, but we can sort of duck type it
[].forEach.call(nodes, function(el, i) {
});
```

