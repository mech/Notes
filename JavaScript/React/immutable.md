# Immutable

> The Dao of Immutability: The true constant is change. Mutation hides change. Hidden change creates chaos. - Eric Elliott

Don't use `Array.shift`, use `Array.slice` instead for immutability.

Immutable data structure with structure sharing.

* [**Immutable as React state**](https://github.com/facebook/immutable-js/wiki/Immutable-as-React-state)
* [ECMAScript proposal](https://github.com/sebmarkbage/ecmascript-immutable-data-structures)
* [react-cursor - Sort of like Baobab](https://github.com/dustingetz/react-cursor/)
* [**Immutable Data Structures and JavaScript**](http://jlongster.com/Using-Immutable-Data-Structures-in-JavaScript)
* [A brief talk about immutability](https://medium.com/@cassiozen/a-brief-talk-about-immutability-and-react-s-helpers-70919ab8ae7c)
* [**The Dao of Immutability**](https://medium.com/javascript-scene/the-dao-of-immutability-9f91a70c88cd)
* [ancient-oak: Immutable data trees](https://github.com/brainshave/ancient-oak)
* [Seamless Immutable](https://github.com/rtfeldman/seamless-immutable)
* [**The power of immutability and React**](https://medium.com/@sharifsbeat/the-power-of-immutability-and-react-daf46f2a5f4d)
* [**Pros and cons of using immutability with React.js**](http://reactkungfu.com/2015/08/pros-and-cons-of-using-immutability-with-react-js/)
* [Immutability in React](http://www.sitepoint.com/immutability-react/)
* [Smart immutable state for React](https://github.com/mistadikay/doob)
* [**Omniscient.js - Simpler UI reasoning with unidirectional data flow and immutable data**](http://omniscientjs.github.io/guides/01-simpler-ui-reasoning-with-unidirectional/)
* [Why should I care about immutable data?](http://www.bennadel.com/blog/2903-why-should-i-care-about-immutable-data-in-reactjs.htm)
* [Immutability in JavaScript](http://www.sitepoint.com/immutability-javascript/)
* [Immutability in React](http://www.sitepoint.com/immutability-react/)
* [Understanding Clojure's Persistent Vectors](http://hypirion.com/musings/understanding-persistent-vector-pt-1)
* [Immutability in Ruby - Part 1](http://blog.deveo.com/immutability-in-ruby-part-1-data-structures/)
* [Immutability in Ruby - Part 2](http://blog.deveo.com/immutability-in-ruby-part-2-domain-models/)

---

* [freezer](https://github.com/arqex/freezer)
* [mori](http://swannodette.github.io/mori/)

```js
// Use map(), filter(), concat() for non-destructive array
// Use concat() instead of push()
let updatedPassengers = this.state.passengers.concat('mech');

// Use Object.assign for getting a new copy instead of mutating existing
// After the assignment, updatedTicket is an entirely different object than this.state.ticket
var updatedTicket = Object.assign({}, this.state.ticket, {flightNo: 'SQ112'});
this.setState({ticket: updatedTicket});
```

If you are using nested object, you are in trouble as neither Array's non-destructive methods nor `Object.assign` makes deep copies. Making a deep clone will be expensive on performance and even impossible to do in some cases. However, React provides a set of utility called Immutability Helpers that can help to update more complex and nested models.

## Values and Objects

* Values, Value Objects - Immutable. `Number`, `Address`
* Objects, Entities - Mutable, with identity. `User`, `Order`

You `Order` has an `id` and can change over time. The items can changed, the amount can change.

The `Address` does not have an `id` and won't likely change over time. The value itself is the identity.

```ruby
class Address
  include Virtus::ValueObject
  
  attribute :street, String
  attribute :zip, String
  attribute :city, String
end
```

## Object.assign - Cheap Immutable Data Structure

Neither the array's non-destructive methods nor `Object.assign` make **deep copies**.

```js
function getOlder(person) {
  return Object.assign({}, person, { age: person.age + 1 })

  // Or ES7 - Spread properties
  return {...person, age: person.age + 1}
}

// Using Babel
// Immutable
function updateUserScore(user, points) {
  return {
    ...user,
    points: user.points + points
  }
}

// Mutable
function updateUserScore(user, points) {
  user.points += points
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

## Array

Let's say you have this structure:

```js
this.state = {
  passengers: [
    'Simmon, Robert A.',
    'Taylor, Kat R.'
  ],
  
  ticket: {
    company: 'Delta',
    flightNo: 'SA0900',
    departure: {
      airport: 'LAS',
      time: '2016-08-12T14:41:10.000Z'
    }
  }
}
```

If you want to add more passengers, you likely use `Array#push` method. Since you are working with a reference, you have just mutated your array destructively. Non-destructive methods like `map`, `filter` and `concat` will give you a new copy instead.

```js
// To add a new passenger
let updatedPassengers = this.state.passengers.concat('Mitchell')
this.setState({ passengers: updatedPassenger })

// To change flight number
let updatedTicket = Object.assign({}, this.state.ticket, { flightNo: '1010' })
this.setState({ ticket: updatedTicket })
```

## Video

* [Immutability: Putting the Dream Machine to work](https://www.youtube.com/watch?v=J-bC20aAat8)