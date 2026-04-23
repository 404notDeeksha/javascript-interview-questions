# Short Circuit Evaluation

It refers to how logical operators like AND (&&), OR (||), and newer operators such as ?? (nullish coalescing) and ?. (optional chaining) evaluate expressions from left to right and stop as soon as the result is determined, without evaluating the rest of the expression

1. **Logical AND (&&)**: it evaluates left expression. If its true, it evaluates right expression. If its false, right expression is not evaluated.
```js
false && doSomething(); // doSomething() is NOT called
```

2. **LOGICAL OR (||)**: it evaluates left expression. If its true, it doesnt goes further to right expression as whole statement is truthy. If its false, right expression is evaluated.
```js
true || doSomething(); // doSomething() is NOT called
```

> This skips evaluating parts of expressions & makes code faster