# Array-like Objects

Array-like objects are objects that have indexed elements (properties with numeric keys) and a non-negative length property, similar to arrays. However, they do not inherit from Array.prototype and therefore lack built-in array methods like push(), pop(), map(), and forEach().

## Features

- Indexed access: Elements can be accessed using numeric indices (e.g., obj, obj[1]).
- Length property: They have a length property indicating the number of elements.
- No array methods: They do not have array methods such as push(), pop(), map(), or forEach().
- Not true arrays: Array.isArray(arrayLikeObject) returns false.

## Examples

- arguments object: Available inside functions, contains all arguments passed to the function.
- DOM collections: Such as NodeList (from document.querySelectorAll) and HTMLCollection (from document.getElementsByTagName).
- Strings: While strings are primitives, they behave like array-like objects because you can access characters by index.

```js
let arrayLike = { 0: 'apple', 1: 'banana', 2: 'cherry', length: 3 };
console.log(arrayLike[1]); // 'banana'
console.log(arrayLike.length); // 3
console.log(Array.isArray(arrayLike)); // false

function showArguments() {
   console.log(arguments); // {0: ..., 1: ..., length: ...}
}
showArguments('a', 'b', 'c');

let divs = document.querySelectorAll('div');
console.log(divs); // NodeList {0: ..., 1: ..., length: ...}
```

## Converting Array-like Objects to Arrays

- Spread operator: [...arrayLikeObject]
- Array.from(): Array.from(arrayLikeObject)
- Object.values(): Object.values(arrayLikeObject) (for objects with numeric keys)