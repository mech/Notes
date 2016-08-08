# Resources

* [**Computer Algorithms - A series**](http://www.stoimen.com/blog/category/algorithms//)
* [Quora: How do I learn Data Structures and Algorithms](http://www.quora.com/How-do-I-learn-Data-Structures-and-Algorithms-2)
* [Timus Online Judge](http://acm.timus.ru/problemset.aspx?space=1&page=all&sort=difficulty)
* [**Visual Algo by NUS Singapore**](http://visualgo.net/)
* [Advanced data structures](http://courses.csail.mit.edu/6.851/spring12/lectures/)
* [DSA with OO patterns in Ruby](http://www.brpreiss.com/books/opus8/)
* [Code Chef's DSA](http://discuss.codechef.com/questions/48877/data-structures-and-algorithms)
* [Data Science Tutorials](https://www.topcoder.com/community/data-science/data-science-tutorials/)
* [A very nice JavaScript recursion tutorial](http://www.htmlgoodies.com/primers/jsp/article.php/3622321)
* [**Data structures for JS**](http://jsclass.jcoglan.com/)
* [Implementing the board game Go with React.js](http://cjlarose.com/2014/01/09/react-board-game-tutorial.html)
* [Computer Science in JavaScript](https://github.com/nzakas/computer-science-in-javascript)
* [Sorting data into a tree](http://stackoverflow.com/questions/8241342/sorting-data-into-a-tree)
* [deque - Extremely fast double-ended queue](https://github.com/petkaantonov/deque)

## Lectures

* [MIT Open Courseware](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-046j-introduction-to-algorithms-sma-5503-fall-2005/video-lectures/)

## Time and Space

* CPU time
* Memory storage space

## Data Structure

Data structures can be characterised by how they store and organise the individual data elements and what operations are available for accessing and manipulating the data.

## Big O Notation

How well an algorithm scale. Not really monitor of speed.

A function f of n f(n) is O(g(n)) if C and n

```
n(n+1) === n^2 + n

f(n)
T(n)
```

Time-complexity

Amortized cost

### O(1)

Order of 1. Execute in the same amount of time regardless of the amount of data. Think `append` or `push` an array or list to add item.

### O(n)

Order of n. Linear growth. Think of a linear search where you need to iterate over n array size to find an item. As n grow, the time take to find the item grow linearly. Worst case scenario where whole array need to be searched.

### O(n^2)

Time to complete will be proportional to the square of amount of data. Common in nested iteration. Bubble sort.

### O(log n)

Binary search. Very fast. More data will half the search time.