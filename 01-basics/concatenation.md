# Concatenation

It is the process of joining two or more strings together to form a single, longer string.

> js concatenates with + operand if either operator is string. with -, * , / js tries to convert(direct) operands to numbers.

```js
let message = "Hello";
message += ", World!"; // "Hello, World!"
let greet = "Good";
let result = greet.concat(" Morning", " Everyone!"); // "Good Morning Everyone!"
const words = ["I", "love", "coding"];
const sentence = words.join(" "); // "I love coding"
```