# Debounce

Debounce ensures that a function is not called again until a certain amount of time has passed since its last execution. If the function is called multiple times within that window, the timer resets each time. Only after the user stops triggering the event for the specified delay does the function execute.

## Implementation

```js
function debounce(func, delay) {
  let timerId;
  return function(...args) {
    clearTimeout(timerId);
    timerId = setTimeout(() => {
      func.apply(this, args);
    }, delay);
  };
}
```

## Usage Example

```js
const search = (query) => {
  console.log('Searching for:', query);
};

const debouncedSearch = debounce(search, 300);

// User types "hello" rapidly
debouncedSearch('h');     // timer starts, gets cleared
debouncedSearch('he');    // timer resets
debouncedSearch('hel');   // timer resets
debouncedSearch('hell');  // timer resets
debouncedSearch('hello'); // timer resets, executes after 300ms
// Output: Searching for: hello (only once)
```

## Interview Questions

### Q: What is the main purpose of debounce?
**A:** To delay function execution until a specified time has passed since the last invocation. Useful for scenarios like search inputs, window resizing, or scroll events where rapid firing would cause performance issues or unnecessary API calls.

### Q: How does debounce work internally?
**A:** It uses a closure to store a timer ID. Each call clears the previous timer and sets a new one. The wrapped function only executes when the timer completes without being interrupted.

### Q: What's the difference between leading edge and trailing edge debounce?
**A:** 
- **Trailing edge** (default): Executes after the delay period passes with no new calls
- **Leading edge**: Executes immediately on the first call, then ignores subsequent calls until the delay passes

```js
function debounce(func, delay, { leading = false } = {}) {
  let timerId;
  return function(...args) {
    if (leading && !timerId) {
      func.apply(this, args);
    }
    clearTimeout(timerId);
    timerId = setTimeout(() => {
      if (!leading) func.apply(this, args);
      timerId = null;
    }, delay);
  };
}
```

### Q: How do you preserve the correct `this` context in debounce?
**A:** Use `func.apply(this, args)` or `func.call(this, ...args)` instead of `func(...args)` to ensure the original `this` binding is maintained.

### Q: How to add a cancel method to debounce?
**A:** Expose a cancel function that clears the timer.

```js
function debounce(func, delay) {
  let timerId;
  const debounced = function(...args) {
    clearTimeout(timerId);
    timerId = setTimeout(() => func.apply(this, args), delay);
  };
  debounced.cancel = () => clearTimeout(timerId);
  return debounced;
}
```

### Q: When should you use debounce vs throttle?
**A:** Use **debounce** when you only care about the final state (e.g., search input, form validation). Use **throttle** when you need regular execution at a fixed rate (e.g., scroll tracking, scroll-based animations, mouse movement).

### Q: How to handle the return value of a debounced function?
**A:** The wrapped function returns `undefined` because it's executed asynchronously via `setTimeout`. To get results, use a callback or Promise.

```js
function debounce(func, delay) {
  let timerId;
  return function(...args) {
    clearTimeout(timerId);
    return new Promise((resolve) => {
      timerId = setTimeout(() => {
        resolve(func.apply(this, args));
      }, delay);
    });
  };
}
```
