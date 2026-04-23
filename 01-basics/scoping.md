# Scope in JavaScript

Scope means current context of execution in which variables, objects & functions are accessible in the code.

1. **Global scope**: Variables declared outside of any function or block are in global scope. They can be accessed from anywhere.
2. **Function (Local) Scope**: Variables declared inside a function are only accessible within that function. They cannot be accessed from anywhere outside the function. Variables declared with var data type are function scoped.
3. **Block Scope**: Introduced in ES6, Variables declared with let and const inside a block (eg., within {}, for loops, if statements, etc.) are only accessible within that block.
4. **Module Scope**: While using Js modules, variables declared inside a module are only accessible within that module unless explicitly exported.

> Scopes work in hierarchy. Inner(child) scopes can access Outer(Parent) scope, not vice versa.
Variable Shadowing: Variables under same name can be declared under different scopes.

```js
let x = 1;  // Global scope

function exampleFunction() {
   let x = 2; // Function scope 
   if (true) {
     let x = 3; // Block scope 
       console.log(x); // 3
      }
   console.log(x); // 2
}
exampleFunction();
console.log(x); // 1
```