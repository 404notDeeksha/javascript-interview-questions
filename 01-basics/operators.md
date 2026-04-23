# Operators in JavaScript

| Operator Type           | Example(s)                                      | Description                                 |
|------------------------|-------------------------------------------------|---------------------------------------------|
| **Arithmetic**         | `+`, `-`, `*`, `/`, `%`, `++`, `--`, `**`       | Math operations (add, subtract, multiply, divide, etc.) |
| **Assignment**         | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=`        | Assign or update variable values            |
| **Comparison**         | `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`  | Compare values and types                    |
| **Logical**            | `&&`, `!`,`Logical OR operator`, `!`                                 | Combine or invert boolean values            |
| **String**             | `+`, `+=`                                       | Join strings together                       |
| **Bitwise**            | `&`,`^`, `~`, `<<`, `>>`, `>>>`, `Bitwise OR operator`     | Works at the binary (bit) level, on single operand             |
| **Conditional (Ternary)** | `condition ? val1 : val2`                    | Short if-else                             |
| **Type**               | `typeof`, `instanceof`                          | Check or test data types                    |
| **Optional Chaining**       | `obj?.prop`, `arr?.[index]`, `func?.()`            | Safely access nested properties, array items, or call functions without throwing an error if an intermediate value is `null` or `undefined` |
| **Nullish Coalescing**      | `a ?? b`                                           | Returns `a` if it's not `null` or `undefined`, otherwise returns `b` (useful for setting default values only when the left side is truly "missing") |

```js
let number = 0;
console.log(number++); //0 number=1 (i++ allows time to increment number later & executes code now)
console.log(++number); //2 number=2 (++i doesnt allow time. it has to increment first, then execute code)
console.log(number); //2 
0 ?? "default"    // returns 0
0 || "default"    // returns "default"

"" ?? "default"   // returns ""
"" || "default"   // returns "default"

null ?? "default" // returns "default"
null || "default" // returns "default"
```