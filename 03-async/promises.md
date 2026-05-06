# Promises ** --

A Promise is an object representing the eventual completion or failure of an asynchronous operation and its resulting value.

## States

- **Pending**: Initial state, neither fulfilled nor rejected
- **Fulfilled**: Operation completed successfully  
- **Rejected**: Operation failed 

## Basic Usage

```js
const promise = new Promise((resolve, reject) => {
  const success = true;
  if (success) {
    resolve('Data fetched!');
  } else {
    reject('Something went wrong');
  }
});

promise
  .then((result) => console.log(result))
  .catch((error) => console.error(error));
```

## Chaining

Promises can be chained using `.then()`. Each `.then()` returns a new Promise.

```js
fetchUser()
  .then((user) => fetchPosts(user.id))
  .then((posts) => console.log(posts))
  .catch((err) => console.error(err));
```

## Promise Combinators

- **Promise.all()**: Waits for all promises to resolve or any to reject
- **Promise.race()**: Settles as soon as any promise settles
- **Promise.allSettled()**: Waits for all promises to settle (resolve or reject)
- **Promise.any()**: Returns first fulfilled promise

```js
Promise.all([p1, p2, p3]).then((results) => console.log(results));
Promise.race([p1, p2]).then((first) => console.log(first));
Promise.allSettled([p1, p2]).then((results) => console.log(results));
```

## Interview Questions

### Q1: What is the difference between `.then()` and `async/await`?

**A:** Both handle promises. `.then()` uses chaining with callbacks, while `async/await` provides synchronous-looking syntax. `async/await` requires try/catch for error handling, making it cleaner for complex async flows.

```js
// .then()
fetchData().then((data) => console.log(data)).catch((err) => console.error(err));

// async/await
async function getData() {
  try {
    const data = await fetchData();
    console.log(data);
  } catch (err) {
    console.error(err);
  }
}
```

---

### Q2: What is the output?

```js
console.log('1');

setTimeout(() => console.log('2'), 0);

Promise.resolve().then(() => console.log('3'));

console.log('4');
```

**A:** `1`, `4`, `3`, `2`

Microtasks (Promises) execute before macrotasks (setTimeout), even if both have 0ms delay.

---

### Q3: What is the difference between `Promise.all()` and `Promise.allSettled()`?

**A:** `Promise.all()` rejects immediately if any promise rejects (fail-fast). `Promise.allSettled()` waits for all promises to settle regardless of outcome and returns an array of result objects with `status: 'fulfilled'` or `status: 'rejected'`.

```js
Promise.all([Promise.resolve(1), Promise.reject('error')])
  .catch((err) => console.log(err)); // 'error'

Promise.allSettled([Promise.resolve(1), Promise.reject('error')])
  .then((results) => console.log(results));
  // [{status: 'fulfilled', value: 1}, {status: 'rejected', reason: 'error'}]
```

---

### Q4: How do you handle errors in a Promise chain?

**A:** Use `.catch()` at the end of the chain, or pass a second argument to `.then()`. `.catch()` catches any rejection in the chain above it.

```js
fetchData()
  .then((data) => processData(data))
  .then((result) => saveResult(result))
  .catch((err) => console.error('Any error above:', err));
```

---

### Q5: What does `Promise.race()` do? Give a use case.

**A:** It returns a promise that settles as soon as any of the input promises settles. Common use case: implementing request timeouts.

```js
const timeout = new Promise((_, reject) =>
  setTimeout(() => reject('Request timed out'), 5000)
);

Promise.race([fetchData(), timeout])
  .then((data) => console.log(data))
  .catch((err) => console.error(err));
```

---

### Q6: What is a common gotcha with `Promise.all()`?

**A:** If any promise rejects, `Promise.all()` immediately rejects and you lose results from already-resolved promises. Use `Promise.allSettled()` when you need all results regardless of individual failures.

---

### Q7: Can you resolve a promise with another promise?

**A:** Yes. When you resolve with a promise, the outer promise adopts the state of the inner one. This is how promise chaining works under the hood.

```js
new Promise((resolve) => {
  resolve(Promise.resolve('done'));
}).then((value) => console.log(value)); // 'done'
```
