# Array

* Shallow copy
* Deep copy

## Splice

Create a new array from existing array.

```js
// Take
// Start from position=3 and take 3 elements
var a = ['a', 'b', 'c', 'd', 'e', 'f', 'g'];
a.splice(3, 3); // d,e,f

// Insertion
// Specifying 0 means nothing to remove
splice(7, 0, newElement);
```

## Sort

`sort()` works very well with strings, but not so well with numbers as it sort lexicographically.

```js
// The ordering function to sort numerically rather than lexicographically
function compare(a, b) {
  return a - b;}

a.sort(compare);
```

## reduce

`reduce()` applies a function to an **accumulator** and successive elements until the end of the array is reached, yielding a single value.

There is also the reverse `reduceRight()`.

## map

```js
function first(word) {
  return word[0];}

var words = ['for', 'your', 'information'];
var acronym = words.map(first).join('');
```

## every and some