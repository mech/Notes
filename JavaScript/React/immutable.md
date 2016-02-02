# Immutable

> The Dao of Immutability: The true constant is change. Mutation hides change. Hidden change creates chaos. - Eric Elliott

Don't use `Array.shift`, use `Array.slice` instead for immutability.

Immutable data structure with structure sharing.

* [react-cursor - Sort of like Baobab](https://github.com/dustingetz/react-cursor/)

## Object.assign - Cheap Immutable Data Structure

```js
function getOlder(person) {
  return Object.assign({}, person, { age: person.age + 1 })

  // Or ES7
  return {...person, age: person.age + 1}
}

// Or ES6 spread and deconstruct
function getOlder({ age, ...other }) {
  return { age: age + 1, ...other }
}
```

```cljs
(defn get-older [person]
  (assoc person :age (+ 1 (:age person))))
```

## Video

* [Immutability: Putting the Dream Machine to work](https://www.youtube.com/watch?v=J-bC20aAat8)