# filter Method

The `filter()` method creates a new array with all elements that pass the test implemented by the provided function.

```js
const numbers = [1, 2, 3, 4, 5, 6];
const evens = numbers.filter(num => num % 2 === 0);
// [2, 4, 6]
```

## Syntax

```js
array.filter(callback(element, index, array), thisArg)
```

- `element`: The current element being processed
- `index` (optional): The index of the current element
- `array` (optional): The array filter was called upon
- Returns a **new array** (does not mutate original)

## Interview Questions

### Q: Does filter mutate the original array?
**A:** No, `filter` returns a new array. The original array remains unchanged.

```js
const arr = [1, 2, 3, 4];
const filtered = arr.filter(n => n > 2);
console.log(arr);        // [1, 2, 3, 4] (unchanged)
console.log(filtered);   // [3, 4]
```

### Q: What happens if no elements pass the filter test?
**A:** It returns an empty array, not `null` or `undefined`.

```js
[1, 2, 3].filter(n => n > 10); // []
```

### Q: How does filter handle sparse arrays (arrays with empty slots)?
**A:** `filter` skips empty slots and does not invoke the callback for them.

```js
const sparse = [1, , 3];
sparse.filter(() => true); // [1, 3] (empty slot is removed)
```

### Q: How to filter an array of objects by a property?
**A:** Use dot or bracket notation inside the callback.

```js
const users = [
  { name: 'Alice', active: true },
  { name: 'Bob', active: false },
  { name: 'Charlie', active: true }
];

const activeUsers = users.filter(user => user.active);
// [{name:'Alice', active:true}, {name:'Charlie', active:true}]
```

### Q: Difference between filter and find?
**A:** `filter` returns **all matching elements** as a new array. `find` returns only the **first matching element** (or `undefined`).

```js
[1, 2, 3, 4].filter(n => n > 2); // [3, 4]
[1, 2, 3, 4].find(n => n > 2);   // 3
```

### Q: How to remove duplicates from an array using filter?
**A:** Use `indexOf` or `Set` inside filter.

```js
const arr = [1, 2, 2, 3, 3, 4];

// Using indexOf
const unique = arr.filter((val, index) => arr.indexOf(val) === index);
// [1, 2, 3, 4]

// Using Set (more efficient)
const unique2 = [...new Set(arr)];
// [1, 2, 3, 4]
```
