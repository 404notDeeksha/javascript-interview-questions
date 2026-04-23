# Data Types in JavaScript

Javascript has basically 2 data types:

## A. Primitive

Immutable, store single values:
1. **Number**: represents integers & floating-point numbers. eg: 7, 5.48.
2. **String**: represents sequence of characters. eg: "Hello".
3. **BigInt**: represents integers with arbitrary precision. number ends with n. Can represent any size of number, limited by memory. eg: 123456123456n
4. **Boolean**: represents logical values - true or false.
5. **Undefined**: variable that has been declared but isnt assigned a value. eg. let value;
6. **Null**: represents Intentional absence of any object value. eg: let value = null;
7. **Symbol**: represent unique, immutable values, often used as object property keys.

## B. Non-Primitive

1. **Object**: They are mutable, are used to store collection of data & more complex entities. eg: Objects(key-value pairs), Arrays(ordered collections), Functions, Dates, Maps, Sets, Regular Expressions(RegExp) etc.

> They store value & hold reference to a memory location.

## Tricky Question:

```js
let x = { a: 1 };  // x points to object1 in memory
let y = x;         // y also points to object1
x = { b: 2 };      // x now points to object2; y still points to previous reference of x, object1 (Reassignment)

let x = { a: 1 };  // x points to object1 in memory
let y = x;         // y also points to object1
x.a = 2;      // Mutation. This changes x & thus y too.
```