# Throttle

Throttle ensures that a function is called at most once in a specified time interval. Unlike debounce, which delays execution until calls stop, throttle guarantees regular execution at fixed intervals while the event is firing.

## Implementation

```js
function throttle(func, limit) {
  let inThrottle;
  return function(...args) {
    if (!inThrottle) {
      func.apply(this, args);
      inThrottle = true;
      setTimeout(() => (inThrottle = false), limit);
    }
  };
}
```

## Usage Example

```js
const trackScroll = () => {
  console.log('Scroll position:', window.scrollY);
};

const throttledScroll = throttle(trackScroll, 200);

window.addEventListener('scroll', throttledScroll);
// Called at most once every 200ms during continuous scrolling
```

## Interview Questions

### Q: What is the main purpose of throttle?
**A:** To limit function execution to at most once per specified interval. Useful for events that fire rapidly and continuously, like scroll, resize, or mouse move events, where you still need periodic updates.

### Q: How does throttle differ from debounce?
**A:** 
- **Debounce**: Waits for a pause in calls before executing (good for search inputs)
- **Throttle**: Executes immediately, then blocks subsequent calls until the interval passes (good for scroll tracking)

```
Debounce:  |--[wait]--> executes (only after calls stop)
Throttle:  |exec|--[wait]-->exec|--[wait]-->exec (regular intervals)
```

### Q: What are the two common throttle implementation approaches?
**A:** 
1. **Timestamp-based**: Uses `Date.now()` to check if enough time has passed
2. **Timer-based**: Uses `setTimeout` to set a flag

```js
// Timestamp-based approach
function throttle(func, limit) {
  let lastCall = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastCall >= limit) {
      lastCall = now;
      func.apply(this, args);
    }
  };
}
```

### Q: How to implement throttle with leading and trailing edge options?
**A:** Leading edge executes immediately on first call. Trailing edge executes once after the interval ends for any calls that were blocked.

```js
function throttle(func, limit, { trailing = false } = {}) {
  let inThrottle;
  let lastArgs;
  let lastContext;

  const execute = () => {
    func.apply(lastContext, lastArgs);
    lastArgs = lastContext = null;
  };

  return function(...args) {
    lastArgs = args;
    lastContext = this;

    if (!inThrottle) {
      func.apply(this, args);
      inThrottle = true;
      setTimeout(() => {
        if (trailing && lastArgs) execute();
        inThrottle = false;
      }, limit);
    } else if (trailing) {
      lastArgs = args;
    }
  };
}
```

### Q: How to preserve `this` context in throttle?
**A:** Use `func.apply(this, args)` to maintain the original calling context.

### Q: When would throttle be a bad choice?
**A:** When you only care about the final result of rapid events. For example, typing in a search box should use debounce because you only want to search after the user finishes typing, not at regular intervals while they're still typing.

### Q: How does throttle handle multiple rapid calls?
**A:** The first call executes immediately. All subsequent calls within the interval are either ignored (leading-only) or queued for execution at the end of the interval (trailing-edge).

### Q: Real-world use cases for throttle?
**A:** 
- Scroll position tracking (infinite scroll, sticky headers)
- Window resize handling (responsive layout calculations)
- Mouse move events (drawing apps, drag and drop)
- Button click rate limiting (prevent double submissions)
- Game loop input handling
