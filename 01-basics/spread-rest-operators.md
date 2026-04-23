# Spread & Rest Operators

## Spread Operator

It "expands" an iterable (like an array or string) into its individual elements. It is commonly used in places where zero or more arguments or elements are expected, such as in function calls, array literals, or object literals. It creates a shallow copy. It creates a new memory.

```js
//Function calls: passing array as function elements
function sum(a, b, c) { return a + b + c; }

const numbers = [1, 2, 3];
sum(...numbers); // 6

//Expanding Arrays:
const arr = [1, 2, 3];
const newArr = [...arr, 4, 5]; // [1, 2, 3, 4, 5]

//Merging Objects:
const obj1 = { a: 1 };
const obj2 = { b: 2 };
const merged = { ...obj1, ...obj2 }; // { a: 1, b: 2 }

//Shallow copy:
let object1 = { name: "Alice", age: 30 };
let object2 = { ...object1 }; // New object in memory
let object3 = object1;
object1.name = "Bob"; //Mutation
console.log(object1, object2, object3); // { name: 'Bob', age: 30 } { name: 'Alice', age: 30 } {name: 'Bob', age: 30}
//object3 refers to same location as of object1
```

## Rest Operators

It gathers multiple elements and condenses them into a single array. It is mainly used in function parameter lists and destructuring assignments to collect the remaining arguments or elements.

```js
//Function Parameter Lists
function logAll(first, ...others) {
console.log(first); // first argument
console.log(others); // array of the rest
}
logAll(1, 2, 3, 4); // 1, [2, 3, 4]

//Destructuring
const [a, b, ...rest] = [1, 2, 3, 4, 5];
// a = 1, b = 2, rest = [3, 4, 5]
```