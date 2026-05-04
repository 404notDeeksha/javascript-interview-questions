# map Method

The `map()` method creates a new array populated with the results of calling a provided function on every element in the calling array.

```js
const numbers = [1, 2, 3];
const doubled = numbers.map(num => num * 2);
// [2, 4, 6]
```

## Syntax

```js
array.map(callback(element, index, array), thisArg)
```

- `element`: The current element being processed
- `index` (optional): The index of the current element
- `array` (optional): The array map was called upon
- Returns a **new array** of same length (does not mutate original)

## Interview Questions

### Q: Does map mutate the original array?
**A:** No, `map` returns a new array. The original array remains unchanged.

```js
const arr = [1, 2, 3];
const mapped = arr.map(n => n * 2);
console.log(arr);     // [1, 2, 3] (unchanged)
console.log(mapped);  // [2, 4, 6]
```

### Q: What is the length of the array returned by map?
**A:** Always the same length as the original array. `map` transforms each element but never adds or removes elements.

```js
[1, 2, 3].map(() => 'x'); // ['x', 'x', 'x'] (length: 3)
```

### Q: Can map return undefined values?
**A:** Yes, if the callback doesn't return anything or explicitly returns `undefined`.

```js
[1, 2, 3].map(n => { if (n > 2) return n; });
// [undefined, undefined, 3]
```

### Q: How to use the index parameter in map?
**A:** The callback receives the index as the second argument.

```js
['a', 'b', 'c'].map((char, index) => `${index}:${char}`);
// ['0:a', '1:b', '2:c']
```

### Q: Difference between map and forEach?
**A:** `map` returns a **new array** with transformed values. `forEach` returns `undefined` and is used for side effects only.

```js
const arr = [1, 2, 3];

const mapped = arr.map(n => n * 2);
console.log(mapped); // [2, 4, 6] (new array)

const forEachResult = arr.forEach(n => n * 2);
console.log(forEachResult); // undefined
```

### Q: When should you NOT use map?
**A:** Don't use `map` when:
1. You are not using the returned array (use `forEach` instead)
2. You need to filter out elements (use `filter` instead)
3. You need to break out of the loop early (use a `for` loop)

```js
// Wrong: ignoring the returned array
[1, 2, 3].map(n => console.log(n));

// Correct: use forEach for side effects
[1, 2, 3].forEach(n => console.log(n));
```

### Q: How to chain map with other array methods?
**A:** Since `map` returns an array, it can be chained with `filter`, `reduce`, `sort`, etc.

```js
const users = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 17 },
  { name: 'Charlie', age: 30 }
];

const adultNames = users
  .filter(user => user.age >= 18)
  .map(user => user.name.toUpperCase());
// ['ALICE', 'CHARLIE']
```
