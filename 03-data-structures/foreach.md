# forEach Method

The `forEach()` method executes a provided function once for each array element. Unlike `map` or `filter`, it always returns `undefined`.

```js
const numbers = [1, 2, 3];
numbers.forEach(num => console.log(num));
// 1
// 2
// 3
```

## Syntax

```js
array.forEach(callback(element, index, array), thisArg)
```

- `element`: The current element being processed
- `index` (optional): The index of the current element
- `array` (optional): The array forEach was called upon
- Returns **undefined** (does not mutate original)

## Interview Questions

### Q: What does forEach return?
**A:** Always returns `undefined`. It is meant for executing side effects, not for transforming data.

```js
const result = [1, 2, 3].forEach(n => n * 2);
console.log(result); // undefined
```

### Q: Can you break out of a forEach loop?
**A:** No, there is no way to stop or break a `forEach` loop other than throwing an exception. Use a `for` loop or `for...of` if you need to break early.

```js
// This does NOT work - forEach will still iterate all elements
[1, 2, 3, 4].forEach(n => {
  if (n === 3) return; // only skips current iteration
  console.log(n);
});

// Use for...of instead for early exit
for (const n of [1, 2, 3, 4]) {
  if (n === 3) break;
  console.log(n); // 1, 2
}
```

### Q: Does forEach mutate the original array?
**A:** `forEach` itself does not create a new array, but if you modify elements by reference inside the callback, the original array can be mutated.

```js
const arr = [1, 2, 3];
arr.forEach((n, i) => arr[i] = n * 2);
console.log(arr); // [2, 4, 6] (mutated)

// Objects can be mutated directly
const users = [{ name: 'Alice' }, { name: 'Bob' }];
users.forEach(user => user.name = user.name.toUpperCase());
// [{name:'ALICE'}, {name:'BOB'}]
```

### Q: forEach vs for loop - when to use which?
**A:** Use `forEach` when:
- You need to perform side effects (logging, DOM manipulation, API calls)
- You want cleaner, functional syntax
- You don't need to break/continue

Use `for` loop when:
- You need to break or continue early
- You need better performance (slightly faster)
- You need to iterate backwards

### Q: How does forEach handle sparse arrays?
**A:** `forEach` skips empty slots and does not invoke the callback for them.

```js
const sparse = [1, , 3];
sparse.forEach(n => console.log(n));
// 1
// 3 (empty slot is skipped)
```

### Q: Can you use await inside forEach?
**A:** You can use `await` inside `forEach`, but it does **not** wait for promises to resolve before continuing. All async operations run in parallel. Use `for...of` for sequential async execution.

```js
// Parallel execution (doesn't wait)
[1, 2, 3].forEach(async n => {
  await fetch(`/api/${n}`);
});

// Sequential execution (waits for each)
for (const n of [1, 2, 3]) {
  await fetch(`/api/${n}`);
}
```

### Q: How to use forEach with objects?
**A:** `forEach` is an array method. To iterate over objects, convert them to arrays first.

```js
const obj = { a: 1, b: 2, c: 3 };

// Using Object.entries
Object.entries(obj).forEach(([key, value]) => {
  console.log(`${key}: ${value}`);
});

// Using Object.keys
Object.keys(obj).forEach(key => {
  console.log(`${key}: ${obj[key]}`);
});
```
