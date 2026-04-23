# Hoisting

Hoisting is a Js mechanism where interpreter appears to move declarations of variables, functions, classes or imports to the top of their scope before code is executed.

- It means certain variables, functions can be accessed before they are actually declared in code.
- **Variable Declarations**: Only declarations are hoisted & not initializations.
- **Function Declarations**: These are fully hoisted, both function's name & body are available throughout the scope where they are declared.
- **Class Declarations**: They are hoisted but not initialized, so referencing them before their declaration causes a ReferenceError.

## Function Hoisting

```js 
foo(); // "Hello"
function foo() {
console.log("Hello");
}
```

> Hoisted means the code runs well at that point of flow (mostly declarations- let,var,const). It makes code more flexible & readable. When variables are declared, memory is assigned to them at top of their scope (Memory allocation phase). var gets undefined & let,const 's memory cant be used, thus Temporal Dead Zone.

Tricky Question:
```js
function sayHi() {
console.log(name);
console.log(age);
var name = 'Deeksha';
let age = 29;
}

sayHi();
//Output undefined Reference Error
```