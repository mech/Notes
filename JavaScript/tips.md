# Tips

```
// querySelectorAll return a NodeList, an array-like list
var nodes = document.querySelectorAll('a');

// In order to iterate it, we cannot use forEach, but we can sort of duck type it
[].forEach.call(nodes, function(el, i) {
});
```

## Netflix autocomplete search

http://www.youtube.com/watch?v=XRYN2xt11Ek

* [Learn RX](http://jhusain.github.io/learnrx/)
* [RxJava](https://github.com/Netflix/RxJava/wiki/Observable)
* [RxJS](https://github.com/Reactive-Extensions/RxJS)

```
var searchResultSets = keyPresses
  .throttle(250)
  .map(function(key) {
    getJSON("/searchResults?q=" + input.value).retry(3)
      .takeUtil(keyPresses)
  }).concatAll();
  
searchResultSets.forEach(function(resultSet) {
  updateSearchResults(resultSet);
});
```