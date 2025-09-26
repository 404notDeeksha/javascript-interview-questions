1. **var/ let/ const variables:**

   | Feature         | var                                | let                                   | const                                      |
   |-----------------|------------------------------------|---------------------------------------|--------------------------------------------|
   | Scope           | Function-scoped or global-scoped   | Block-scoped                          | Block-scoped                               |
   | Hoisting        | Yes (initialized as `undefined` at top of its scope)   | Yes (but not initialized, Reference Err due to "temporal dead zone" (TDZ) applies)| Yes (but not initialized, TDZ applies)     |
   | Redeclaration   | Allowed within the same scope      | Not allowed in the same scope         | Not allowed in the same scope              |
   | Reassignment    | Allowed                            | Allowed                               | Not allowed (value is constant)            |
   | Initialization  | Optional                           | Optional                              | Required                                   |
   | Use Case        | Legacy code, old browsers          | Modern JS, variables that change      | Constants, values that never change   


```js
// "===== HOISTING & TDZ ====="

// VAR is hoisted and initialized as undefined
console.log("var before declaration:", myVar); // undefined
var myVar = "I am var";

// LET and CONST are hoisted but in TDZ (cannot access before declaration)
try {
    console.log("let before declaration:", myLet); // ReferenceError
} catch (err) {
    console.log("let before declaration:", err.message);
}

try {
    console.log("const before declaration:", myConst); // ReferenceError
} catch (err) {
    console.log("const before declaration:", err.message);
}

let myLet = "I am let";
const myConst = "I am const";

// ===== SCOPE & SHADOWING =====

function scopeTest() {
    var functionVar = "function-scoped var";
    let blockLet = "block-scoped let";
    const blockConst = "block-scoped const";

    if (true) {
        var functionVar = "redeclared var inside block";
        let blockLet = "new let inside block";
        const blockConst = "new const inside block";

        console.log("Inside block:");
        console.log("var:", functionVar);    // redeclared var
        console.log("let:", blockLet);       // new block-scoped let
        console.log("const:", blockConst);   // new block-scoped const
    }

    console.log("Outside block:");
    console.log("var:", functionVar);       // redeclared var persists
    console.log("let:", blockLet);          // original let remains
    console.log("const:", blockConst);      // original const remains
}

scopeTest();

// ===== REDECLARATION & REASSIGNMENT =====

// VAR
var a = 1;
var a = 2; // redeclaration allowed
a = 3;     // reassignment allowed
console.log("var a:", a);

// LET
let b = 10;
~let b = 20;~ // SyntaxError: cannot redeclare
b = 15;       // reassignment allowed
console.log("let b:", b);

// CONST
const c = 100;
~~const c = 200;~~ // SyntaxError: cannot redeclare
~c = 300;~       // TypeError: cannot reassign
console.log("const c:", c);

// ===== INITIALIZATION =====

// var and let: optional
var p;
console.log("var p before init:", p); // undefined
p = 5;
console.log("var p after init:", p); // 5

let q;
console.log("let q before init:", q); // undefined
q = 10;
console.log("let q after init:", q); // 10

// const: must initialize
// const r; // SyntaxError
const r = 50;
console.log("const r:", r);

```

2. **Hoisting**:

- JS moves declarations to the top of their scope, not initializations.
- Functions are hoisted completely.

```js
console.log(a); // undefined (hoisted but uninitialized)
var a = 5;

sayHi(); // "Hello" (function hoisting)
function sayHi() {
  console.log("Hello");
}
```
> When variables are declared, memory is assigned to them at top of their scope (Memory allocation phase). 
   var gets undefined & let,const 's memory cant be used, thus Temporal Dead Zone.

3. **Data Types**:

- Primitive Types (immutable): string, number, boolean, null, undefined, symbol, bigint.
- Reference Types: object, array, function, date, RegExp, etc.

```js
console.log(typeof "hi"); // string
console.log(typeof 123); // number
console.log(typeof null); // object (quirk!)
console.log(typeof undefined); // undefined
```

4. **Type Coercion**:

- Explicit coercion:(Type Casting) using String(), Number(), Boolean().
- Implicit coercion:(Type Coercion) when JS auto-converts.

```js
console.log(5 + "5");   // "55" (number → string)
console.log("5" - 2);   // 3 (string → number)
console.log(+"42");     // 42 (string to number)
```

5. **Concatenation**: Adding two strings. 

- using `+`, `.join(patternToJoin)`, `.concat("new_string")`

6. **Equality (== vs ===)**: 

- Loose Equality : `==`: checks equality with type coercion.
- Strict Equality : `===`: checks equality without coercion (strict).

```js
console.log(0 == "0"); // true
console.log(0 === "0"); // false
console.log(null == undefined); // true
console.log(null === undefined); // false
```

7. **Truthy & Falsy Values**:

- Falsy values in JS: false, 0, -0, 0n (BigInt zero), "", null, undefined, NaN. Everything else is truthy.


```js
if ("hello") console.log("truthy"); // runs
if (0) console.log("falsy"); // not run
```

8. **Pass by Value vs Pass by Reference**:

- Primitives are copied by value.
- Objects/Arrays/Functions are copied by reference (actually, reference itself is copied).

```js
let a = 10;
let b = a;
b = 20;
console.log(a); // 10 (unchanged)

let obj1 = { name: "Deeksha" };
let obj2 = obj1;
obj2.name = "Sharma";
console.log(obj1.name); // "Sharma"
```

9. **Immutability of Primitives**: 

Primitives can’t be altered directly. They are Immutable.  Assigning creates a new value.
```js
let str = "hello";
str[0] = "H"; 
console.log(str); // "hello" (unchanged)

// Right way to do this is 
let str = "hello";
str = "H" + str.slice(1); 
console.log(str); // "Hello"

```

10. **The typeof, instanceof, and Object.prototype.toString**: 

- `typeof`: good for primitives, but quirks with null (null is an object).
- `instanceof`: checks prototype chain. Good for objects, not primitives, because it works well with objects because it checks the prototype chain.
- `Object.prototype.toString.call()`: accurate type check than above two.

```js
console.log(typeof []); // object
console.log([] instanceof Array); // true
123 instanceof Number;   // false (primitives fail)
new Number(123) instanceof Number; // true (object wrapper)
console.log(Object.prototype.toString.call([])); // [object Array]
```
> Prototype chain = the path JavaScript follows to find a property or method in parent objects.
// Array - Path
- arr  (your object)
 │
 ├─> Array.prototype   (methods like push, pop, map, toString…)
 │
 ├─> Object.prototype  (methods like hasOwnProperty, toString…)
 │
 └─> null   (end of the chain)

11. **Undefined vs Null**:

- `undefined`: variable declared but not assigned.
- `null`: intentional absence of a value.

```js
let x;
console.log(x); // undefined
let y = null;
console.log(y); // null
```

12. Function Declaration - Named Function with function keyword. Hoisted to top of its scope. `this` is dynamic — depends on the caller (global, object, or undefined in strict).   

13. Function Expression - Function is assigned to a variable. can be named or anonymous. Not Hoisted because variable isnt hoisted. Allocated memory only at runtime (Execution Phase).

14. Arrow Function - does not have its own `this` binding.  `this` is lexical — it’s locked to the this value of the scope where they were created (They lexically inherit this from where they were created.)

- Strict mode only changes the global fallback: no auto-binding to window, instead this = undefined

15. Default Parameter: used to avoid undefined. it gets executed only at runtime on fn call.

```js
function add(a = 0, b = 0) {
  return a + b;
}

add(5); // 5 + 0 = 5
```

16. Rest Parameters: all extra arguements get packed in one array. different than arguements. 
```js
function sum(...nums) {
  return nums.reduce((a, b) => a + b, 0);
}

// REST v/s Arguments

function oldWay(a, b) {
  console.log(arguments); // {0:1, 1:2, 2:3}
}

function newWay(a, b, ...rest) {
  console.log(rest); // [3]
}

oldWay(1, 2, 3);  // gives array like object
newWay(1, 2, 3);
```

17. Spread Operator - emptying the array /object items seperately. copies/ overwrites properties while merging.
```js
const obj1 = {a: 1, b: 2};
const obj2 = {...obj1, b: 99};
console.log(obj2); // {a:1, b:99}
```

18. 



