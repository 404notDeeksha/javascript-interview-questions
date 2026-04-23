# Callback Functions

It is any function passed as an argument to another function, which is then invoked inside the outer function to complete some kind of routine or action.

```js
function greet(name, callback) {
console.log('Hello, ' + name);
callback();
}

function sayGoodbye() {
console.log('Goodbye!');
}

greet('Alice', sayGoodbye);
// Output:
// Hello, Alice
// Goodbye!
```