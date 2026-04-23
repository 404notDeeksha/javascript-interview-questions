# Variables: var, let, const

| Feature         | var                                | let                                   | const                                      |
|-----------------|------------------------------------|---------------------------------------|--------------------------------------------|
| Scope           | Function-scoped or global-scoped   | Block-scoped                          | Block-scoped                               |
| Hoisting        | Yes (initialized as `undefined` at top of its scope)   | Yes (but not initialized, Reference Err due to "temporal dead zone" (TDZ) applies)| Yes (but not initialized, TDZ applies)     |
| Redeclaration   | Allowed within the same scope      | Not allowed in the same scope         | Not allowed in the same scope              |
| Reassignment    | Allowed                            | Allowed                               | Not allowed (value is constant)            |
| Initialization  | Optional                           | Optional                              | Required                                   |
| Use Case        | Legacy code, old browsers          | Modern JS, variables that change      | Constants, values that never change        |

## Hoisting

**var**: It is an implicit (default) keyword.

```js
console.log(a); // Output: undefined
var a = 10; // or a=10
console.log(a); // Output: 1

console.log(b); // ReferenceError: Cannot access 'b' before initialization
let b = 20;
console.log(b); // This line won't run

console.log(c); // ReferenceError: Cannot access 'c' before initialization 
const c = 30;
console.log(c); // This line won't run
```

Tricky Question:
```js
for (var i = 0; i < 3; i++) {
setTimeout(() => console.log(i), 1);
}

for (let i = 0; i < 3; i++) {
setTimeout(() => console.log(i), 1);
}
//Output 333 012
```