# typeof Operator

It returns a string describing datatype of variable or value in picture. It is used for debugging, checking variables before performing operations.

```js
typeof 42;           // "number"
typeof "hello";      // "string"
typeof true;         // "boolean"
typeof undefined;    // "undefined"
typeof {a:1};        // "object"
typeof [1,2,3];      // "object"   // Arrays are also objects. so, Array.isArray(value) is preferred
typeof null;         // "object"   // This is a known quirk in JavaScript
typeof function(){}; // "function"
```

> cant differentiate between arrays or Objects & null or Objects.
isNaN() returns true for non number values-which cant convert to numbers. true for number values.
isNaN('a')  //true
isNaN(2)    //false
isArray([])   //true