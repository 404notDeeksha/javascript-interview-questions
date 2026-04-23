# Closures

A closure in JavaScript is a feature where an inner function has access to the references (variables and parameters) of its outer (enclosing function)—even after the outer function has finished executing.

When a function is defined inside another function, the inner function forms a closure. The closure gives the inner function access to:

1. Its own scope (variables defined inside it).
2. The scope of the outer function.
3. The global scope.

```js
function outerFunction() {
let outerVariable = 'I am from the outer function';

  function innerFunction() {
   console.log(outerVariable);
  }

return innerFunction;
}

const closureExample = outerFunction();
closureExample(); // Output: I am from the outer function
```

## var vs let in Closures

- With var: Closure stores reference to the same variable. That variable changes → all functions see latest value
- With let: Closure stores different variable per iteration. Each one is frozen to its own value

"In a for loop, let creates a new lexical environment for each iteration. Each function closes over a different binding of i, whereas var uses a single shared binding."

```js
for (var i = 0; i < 3; i++) {
  funcs.push(function() {
    console.log(i);
  });
} // 3 3 3

for (let i = 0; i < 3; i++) {
  funcs.push(function() {
    console.log(i);
  });
} // 0 1 2
```