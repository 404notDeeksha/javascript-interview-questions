# Type Casting & Type Coercion

These refer to changing value from one datatype to another in js.

1. **Type Casting (Explicit Type Conversion)**: in this, user explicitly converts a value from one type to another using built-in functions or methods.

```js
let num = "123";
let convertedNum = Number(num); // Explicitly converts string to number
Boolean(null);  // false
Boolean(undefined) // false
```

2. **Type Coercion (Implicit Type Conversion)**: here, js automatically converts a value from one type to another as needed, usually during operations or comparisons. Often done when using operators like +, ==, or conditional statements.

```js
let result = "5" + 2; // JavaScript concatenates with + operator if either operand is string -> 2 to "2", result is "52"
let isEqual = (5 == "5"); // JavaScript coerces "5" to 5, result is true
console.log([] == ![]);         // true
// [] is truthy, but ![] is false. 
// [] == false → [] coerced to "", false to 0, 
// "" == 0 → true.
console.log('d'-0);  //NaN
// 'd'->string to number but string => number not possible
// Nan-0 = Nan
```