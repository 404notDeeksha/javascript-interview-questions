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

## Interview Questions

### Q: What exactly gets hoisted in JavaScript?
**A:** Declarations, not initializations. Variable declarations (`var`, `let`, `const`), function declarations, and class declarations are hoisted. Only `var` gets initialized with `undefined`. `let` and `const` remain in the Temporal Dead Zone (TDZ).

```js
console.log(a); // undefined (hoisted, initialized with undefined)
console.log(b); // ReferenceError (hoisted but in TDZ)
console.log(c); // ReferenceError (hoisted but in TDZ)

var a = 10;
let b = 20;
const c = 30;
```

### Q: Are function expressions hoisted?
**A:** No. Only function declarations are hoisted. Function expressions behave like variable declarations.

```js
sayHello(); // "Hello!" (function declaration hoisted)
function sayHello() { console.log("Hello!"); }

sayBye(); // TypeError: sayBye is not a function
var sayBye = function() { console.log("Bye!"); };
```

### Q: What is the Temporal Dead Zone (TDZ)?
**A:** The period between entering scope and the actual declaration of a `let` or `const` variable. Accessing the variable during TDZ throws a `ReferenceError`.

```js
console.log(x); // ReferenceError (in TDZ)
let x = 5;
console.log(x); // 5 (TDZ ends)
```

### Q: How does hoisting work with `var` vs `let`/`const`?
**A:** 
- `var`: Hoisted and initialized with `undefined`. Accessible before declaration.
- `let`/`const`: Hoisted but **not initialized**. Accessing before declaration throws `ReferenceError`.

```js
console.log(a); // undefined
var a = 1;

console.log(b); // ReferenceError
let b = 2;
```

### Q: Are arrow functions hoisted?
**A:** No, because they are assigned to variables (function expressions).

```js
add(1, 2); // TypeError: add is not a function
const add = (a, b) => a + b;
```

### Q: What gets hoisted first: functions or variables?
**A:** Function declarations are hoisted before variable declarations. If both have the same name, the function takes precedence.

```js
console.log(foo); // ƒ foo() {}
var foo = 10;
function foo() {}
console.log(foo); // 10 (assignment overwrites)
```

### Q: What about `typeof` on a variable in TDZ?
**A:** `typeof` throws `ReferenceError` for variables in TDZ (unlike undeclared variables which return `'undefined'`).

```js
typeof undeclaredVar; // 'undefined' (safe)
typeof x;             // ReferenceError (TDZ)
let x = 5;
```

### Q: How does hoisting work with `class` declarations?
**A:** Classes are hoisted but remain uninitialized (like `let`). Using them before declaration throws `ReferenceError`.

```js
const p = new Person(); // ReferenceError
class Person {}
```

### Q: Does hoisting happen across scopes?
**A:** Hoisting only moves declarations to the top of their **own scope**, not across different scopes.

```js
function test() {
  if (true) {
    console.log(x); // ReferenceError (block scope TDZ)
    let x = 5;
  }
}
```

### Q: What happens with duplicate `var` declarations?
**A:** `var` allows duplicate declarations. The last assignment wins. `let`/`const` throw `SyntaxError` on duplicate declarations in the same scope.

```js
var a = 1;
var a = 2;
console.log(a); // 2

let b = 1;
let b = 2; // SyntaxError: Identifier 'b' has already been declared
```

### Q: Are `import` statements hoisted?
**A:** Yes, ES modules are hoisted and evaluated first before any other code runs.

```js
useModule(); // works because import is hoisted
import { useModule } from './module.js';
```