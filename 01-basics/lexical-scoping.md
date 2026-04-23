# Lexical Scoping

Lexical scoping (also called static scoping) is a fundamental concept in JavaScript that determines how variable names are resolved in nested functions. In lexical scoping, the scope of a variable is determined by its position within the source code—specifically, where it is declared—not by where or how functions are called.

## How it works?

When a function is defined inside another function, the inner function has access to variables declared in its own scope as well as in all of its outer (parent) scopes, up to the global scope. This relationship is established at the time of function declaration, not at the time of function invocation.

```js
function outerFunction() {
  let outerVariable = 'I am outside!';
  function innerFunction() {
   outerVar
    console.log(outerVariable); // 'I am outside!'
  }
  innerFunction();
}
outerFunction();
```

## Scope Chain

When JavaScript looks up a variable, it starts in the current scope. If the variable isn't found, it moves up to the parent scope, and continues this process until it reaches the global scope or finds the variable.

> JavaScript uses lexical scope, so functions always have access to variables where they were defined, not where they are called.

## Lexical Scoping and Closures

Closures are functions that "remember" their lexical scope, even after the outer function has finished executing. This allows inner functions to retain access to variables from their parent scopes.

```js
function counter() {
  let count = 0;
   return function() {
   count++;
   console.log(count);
  }
}
const increment = counter();
increment(); // 1
increment(); // 2 closure remembers its Lexical scope even after outer fn (counter()) finishes execution
```

Tricky Question:
```js
let funcs = [];
for (var i = 0; i < 3; i++) {
  funcs.push(function() {
    console.log(i);
  });
}
funcs[0]();
funcs[1]();
funcs[2]();
//Output: 
//3
//3
//3
//if i -> let , output => 0 1 2

let funcs = [];

for (var i = 0; i < 3; i++) {
  (function(j) {
    funcs.push(function() {
      console.log(j);
    });
  })(i);
}

funcs[0](); // 0
funcs[1](); // 1
funcs[2](); // 2
```