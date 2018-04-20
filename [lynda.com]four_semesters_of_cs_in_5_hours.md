# Lynda.com: Four Semesters of Computer Science in 5  Hours

https://www.lynda.com/JavaScript-tutorials/Four-Semesters-Computer-Science-5-Hours/604270-2.html

> * Author: Brian Holt
> * Released: 6/2/2017
> * Duration: 4h 46m
> * Skill Level: Intermediate

> Get a practical introduction to computer science concepts and take your knowledge of JavaScript to the next level. This course starts by exploring recursion, followed by how to use sorting algorithms. Next, the main elements of data structure interfaces are explained followed by demonstrations of how to implement list, tree, and table structures. Then, functional programming is covered, including use of map, reduce, and filter. For each section of the course, exercises are provided so you can practice.

> Note: This course was created by Frontend Masters. It was originally released on 07/12/2016. We're pleased to host this training in our library.

> Topics include:
> * Big O
> * Recursion
> * Sort: Bubble, insertion, and merge,
> * Quicksort
> * Median values
> * Interfaces
> * Set, map, stack, and queue
> * Array lists and linked lists
> * Binary search tree
> * AVL tree
> * Single rotation and double rotation
> * Hash table
> * Functional programming
> * Map, reduce, and filter


## 1. Big O and Resursion
### 1.1 Introduction
* [http://bit.ly/4semesters](http://bit.ly/4semesters)
* clickbait title
* Some knowledge of ES6 required
* https://mitpress.mit.edu/books/introduction-algorithms

### 1.2 Big O
> Think of the O as a vacuum that sucks in all the unimportant information and just leaves you with the important stuff. 

### 1.3 Finding Big O
* O(n): without exponential terms
* O(n<sup>2</sup>): nested loop
* O(1)
* O(log n): merge sort, quick sort

### 1.4 Recursion
* a bit of cost because of many callings of functions
* readibility over performance, and refactor it later if you figure it's a big bottleneck 

### 1.5 Recursion Example
* Codepen : http://codepen.io/btholt/pen/rxwEVQ?editors=001

### 1.6 Exercise 1: Recursion
* Factorial: 
```
function factorial(n) {
    if (n < 2) return 1;
    return n * factorial(n-1;)
}
```