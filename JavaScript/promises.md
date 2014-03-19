# Promises

* [Promises, promises](http://wibblycode.wordpress.com/2012/11/21/promises-promises/)

```
function getProfileImage(username) {
  var promise = new Promise();
  var image = new Image();
  
  image.addEventListener('load', function(event) {
    promise.resolve(this);
  });
  
  image.addEventListener('error', function(event) {
    promise.reject(new Error('Failed to load image'));
  });
  
  return promise;
}
```