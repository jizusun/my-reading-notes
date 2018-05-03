# MDN web docs > JavaScript

https://developer.mozilla.org/en-US/docs/Web/JavaScript

> JavaScript(JS) is a lightweight interpreted or JIT-compiled programming language with first-class functions. ... JavaScript is a prototype-based, multi-paradigm, dynamic language, supporting object-oriented, imperative, and declarative(e.g. functional programming) styles.

> As of 2012, all modern browsers fully support ECMAScript 5.1.
> On June 17, 2015, ECMA International published the sixth major version of ECMAScript which officially called ECMAScript 2015, and was initially refered to as ECMAScript 6 or ES6.

# JavaScript Tutorial

## JavaScript first steps
## JavaScript building blocks
## Introducing JavaScript objects
## JavaScript Guide
## Client-side web APIs
## A re-introduction to JavaScript
## JavaScript data structures
## Equality comparison and sameness
## Inheritance and the prototype chain
## Strict mode
## JavaScript typed arrays
## Memory Management
## Concurrency model and Event loop

# JavaScript Reference

## Standard Objects

### [Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)

#### Constructor
* `{ nameValuePair1[, nameValuePair2,[, ... nameValuePairN] ] ] }`
* `new Object([value])`: create a wrapped object for the given value

#### Properties
* `Object.length`
* `Object.prototype`: not inheriting from this when created by `Object.create(null)`
* `Object.prototype.constructor`
* `Object.prototype.__proto__` (not standardized)

#### Methods
* `Object.assign(target, ...sources)`
    * to copy all enumerable own properties from one or more source objects to a target object
    * uses `[[Get]]` on the source and `[[Set]]` on the target
    * can be used for: shallow clone, merging objects
* `Object.create(proto[, propertiesObject])`
    - create a new object, using an existing object to provide the newly object's `_proto__`
* `Object.defineProperty(obj, props)`
    - `props` is an object whose own enumerable properties constitute descriptors to be defined or modified
    - `configurable`, `enumerable`, `value`, `writable`, `get`, `set`
* `Object.entries()`
* `Object.freeze()`
* `Object.getOwnPropertyDescriptor()`
* `Object.getOwnPropertyDescriptors()`
* `Object.getOwnPropertyNames()`
* `Object.getOwnPropertySymbols()`
* `Object.getPrototypeOf()`
* `Object.is()`
* `Object.isExtensible()`
* `Object.isFrozen()`
* `Object.isSealed()`
* `Object.keys()`: only names of own enumerable properties
* `Object.preventExtensions()`
* `Object.seal()`
* `Object.setPrototypeOf()`
* `Object.values()`
* `Object.prototype.hasOwnProperty()`
* `Object.prototype.isPrototypeOf()`
* `Object.prototype.propertyIsEmumerable()` 
* `Object.prototype.toLocaleString()`
* `Object.prototype.toString()`
* `Object.prototype.watch()`

### References
* [Working with Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)
* [Introducing JavaScript objects](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects)

## Expression and operators
## Statements and declarations
## Functions
