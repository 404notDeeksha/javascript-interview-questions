# Functions in JavaScript

A function in JavaScript is a reusable block of code designed to perform a particular task. Functions help organize and modularize code, making it easier to maintain and reuse.

A function definition needs:
1. The function's name (optional for anonymous functions).
2. Parameters (inputs the function can accept).
3. The code to execute (inside curly braces).
4. Optionally, a return value.

## Ways to Define Functions

1. **Function Declaration (Statement)**: Named Function with function keyword. Hoisted to top of its scope.
```js
function greet(name) {
return "Hello, " + name;
}
greet("Deeksha");
```

2. **Function Expression**: Function is assigned to a variable. can be named or anonymous. Not Hoisted. Will give Reference Err due to TDZ.
```js
const greet = function(name) {
return "Hello, " + name;
};
```

3. **Arrow Function Expression (ES6)**: does not have its own `this` binding.
```js
const greet = (name) => "Hello, " + name;
```

4. **Method Definition (in Objects)**: functions are defined inside objects as methods.
```js
const person = {
greet(name) {
   return "Hello, " + name;
   }
};
```

5. **Function Constructor**: Used to dynamically create a new function from a string of code. defines function at runtime.
```js
const greet = new Function("name", "return 'Hello, ' + name;");
greet("World"); // Returns "Hello, World"
```

6. **Generator and Async Functions**: Special types of functions for advanced use cases:
   - **Generator function**: uses function and yield.
   - **Async function**: uses async and returns a Promise.

```js
async function fetchData() {
   const response = await fetch('https://api.example.com/data');
   const data = await response.json();
   return data;
}

fetchData().then(data => {
   console.log(data);
});
```