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
// let b = 20; // SyntaxError: cannot redeclare
b = 15;       // reassignment allowed
console.log("let b:", b);

// CONST
const c = 100;
// const c = 200; // SyntaxError: cannot redeclare
// c = 300;       // TypeError: cannot reassign
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

6. 

