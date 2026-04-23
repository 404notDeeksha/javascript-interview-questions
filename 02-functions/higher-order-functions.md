# Higher Order Functions (HOFs)

Higher-order functions are functions that either take one or more functions as arguments, return a function as a result, or both. Array methods like array.map(), array.filter(), array.reduce() are Higher Order Functions.

## Functions that return another function

```js
function multiplier(factor) {
  return function(num) {
   return num * factor;
   };
}
//multiplier return a fn
const double = multiplier(2);
console.log(double(5)); // 10
```

## Functions that take function as argument

```js
function greet(callback) {
   console.log("Hello!");
   callback();
}
function sayBye() {
console.log("Goodbye!");
}
greet(sayBye); // Output: Hello! Goodbye!
```