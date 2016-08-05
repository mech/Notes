# Clojure

* [flatmap](http://2014.flatmap.no/)
* [ClojureScript workshop](https://www.niwi.nz/cljs-workshop/#_more)
* [The Unofficial Guide to Rich Hickey's Brain](http://www.flyingmachinestudios.com/programming/the-unofficial-guide-to-rich-hickeys-brain/)

Clojure is:

* Functional, but not as pure like Haskell
* Dynamically strongly typed
* Hosted - Designed to hosted on platform like JVM, CLR, etc.
* Atomic Succession Model
* Lisp

Core feature:

* Representation - Not XML and JSON. Using `edn`.
* Value - Datomic, history, immutable data
* Operation
* Interop
* Simplicity
* Integration

Companies:

* [Relevance](http://thinkrelevance.com/)


```
new Widget("red"); 	// Java
(Widget. "red")		// Clojure

Math.PI					// Java
Math/PI					// Clojure

rnd.nextInt;			// Java
(.nextInt rnd)			// Clojure
```



## Map

```
(def m {:a 1 :b 2 :c 3})
(m :b) -> 2 ;also (:b m)
(keys m) -> (:a :b :c)
(assoc m :d 4 :c 42) -> {:d 4, :a 1, :b2, :c 42}
```

## Set

```
(use clojure.set)
(def color #{"red" "green" "blue"})
```

## List

## Vector

Function parameters are specified in a vector: `[]` instead of a list: `()`.

```
(defn hello-world [username]
  (println (format "Hello, %s" username)))
```

Here I define a vector `v` which has 3 elements. A number `42`, a symbol `:rabbit` and another vector `[1 2 3]`:

    (def v [42 :rabbit [1 2 3]])
    (v 1) -> :rabbit
    (peek v) -> [1 2 3]
    (pop v) -> [42 :rabbit]
    (subvec v 1) -> [:rabbit [1 2 3]]
    (contains? v 0) -> true

## Sequences

```
(drop 2 [1 2 3 4 5]) -> (3 4 5)

(take 9 (cycle [1 2 3 4]))
-> (1 2 3 4 1 2 3 4 1)

(interleave [:a :b :c :d :e] [1 2 3 4 5])
-> (:a 1 :b 2 :c 3 :d 4 :e 5)

(partition 3 [1 2 3 4 5 6 7 8 9])
-> ((1 2 3) (4 5 6) (7 8 9))

(map vector [:a :b :c :d :e] [1 2 3 4 5])
-> ([:a 1] [:b 2] [:c 3] [:d 4] [:e 5])

(for [x (range 2) y (range 3)] [x y])
=> ([0 0] [0 1] [0 2] [1 0] [1 1] [1 2])
```

## Functional Programming

Function returns something. That's how you operate on it.





