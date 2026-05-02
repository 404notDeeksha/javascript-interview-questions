# `this` Binding, call, apply & bind

## The `this` Keyword

`this` refers to the object that is executing the current function. Its value is determined by **how** a function is called, not where it is defined.

### Binding Rules

1. **Global Context**: In non-strict mode, `this` refers to the global object (`window` in browsers). In strict mode, it is `undefined`.
2. **Object Method**: When a function is called as a method of an object, `this` refers to that object.
3. **Standalone Function**: Same as global context—`window` (non-strict) or `undefined` (strict).
4. **Event Handler**: `this` refers to the element that received the event.
5. **Arrow Functions**: Do not have their own `this`. They inherit `this` lexically from the enclosing scope at the time they are defined.
6. **Constructor (new)**: `this` refers to the newly created instance.

```js
const user = {
  name: 'Deeksha',
  greet() {
    console.log(this.name);
  }
};

user.greet(); // "Deeksha" — `this` is `user`

const greetRef = user.greet;
greetRef(); // undefined (or window.name) — `this` is global, not `user`, method extraction => Becomes plain call.
```

### Arrow Function Gotcha

```js
const person = {
  name: 'Deeksha',
  greet() {
    setTimeout(() => {
      console.log(this.name); // arrow inherits `this` from greet()
    }, 100);
  }
};

const person2 = {
  name: 'Deeksha',
  greet() {
    setTimeout(function() {
      console.log(this.name); //  regular plain function gets global `this`
    }, 100);
  }
};

person.greet(); // "Deeksha" 
person2.greet();  // undefined
```

## Explicit Binding: call, apply & bind

These methods allow you to manually set what `this` refers to when invoking a function.

### call()

Invokes the function immediately with a specified `this` value and arguments passed **individually**.

```js
function introduce(age, city) {
  console.log(`Hi, I'm ${this.name}, ${age} years old from ${city}`);
}

const user = { name: 'Deeksha' };

introduce.call(user, 25, 'Bangalore');
// Output: Hi, I'm Deeksha, 25 years old from Bangalore
```

### apply()

Same as `call()`, but accepts arguments as an **array** (or array-like object).

```js
function introduce(age, city) {
  console.log(`Hi, I'm ${this.name}, ${age} years old from ${city}`);
}

const user = { name: 'Deeksha' };

introduce.apply(user, [25, 'Bangalore']);
// Output: Hi, I'm Deeksha, 25 years old from Bangalore
```

**Common use case:** Finding max in an array (before spread operator).
```js
const numbers = [5, 6, 2, 3, 7];
Math.max.apply(null, numbers); // 7
```

### bind()

Returns a **new function** with `this` permanently bound to the provided value. Does **not** invoke immediately.

```js
const user = { name: 'Deeksha' };

function greet() {
  console.log(`Hello, ${this.name}`);
}

const boundGreet = greet.bind(user);
boundGreet(); // "Hello, Deeksha"

// Useful for callbacks
const button = document.querySelector('button');
button.addEventListener('click', boundGreet);
```

### Partial Application with bind()

`bind()` also supports pre-setting arguments (currying/partial application):

```js
function multiply(a, b) {
  return a * b;
}

const double = multiply.bind(null, 2);
double(5); // 10
double(10); // 20
```

## Polyfill for `bind()`

A polyfill replicates native `bind()` behavior: returns a new function with `this` bound, supports partial application, and handles `new` keyword invocation.

```js
Function.prototype.myBind = function(context, ...args) {
  const fn = this; // the function being bound

  function boundFn(...newArgs) {
    // If called with `new`, `this` is the new instance — ignore the bound context
    if (this instanceof boundFn) {
      return new fn(...args, ...newArgs);
    }
    return fn.apply(context, [...args, ...newArgs]);
  }

  // Preserve prototype chain for `new` usage
  boundFn.prototype = Object.create(fn.prototype);

  return boundFn;
};

//or

Function.prototype.myBind = function(context) {
  const fn = this;

  return function(...args) {
    return fn.apply(context, ...args);
  };
};

```

### How It Works

1. **Capture `this`**: The function on which `myBind` is called (`fn`).
2. **Return a wrapper**: `boundFn` merges pre-set arguments (`args`) with later arguments (`newArgs`).
3. **`apply` for `this` binding**: Calls the original function with the bound `context`.
4. **`new` keyword support**: If `boundFn` is invoked with `new`, the instance check (`this instanceof boundFn`) overrides the bound context and constructs a new object.
5. **Prototype chain**: `Object.create(fn.prototype)` ensures instances created via `new boundFn()` inherit from the original function's prototype.

### Usage Example

```js
function greet(greeting, punctuation) {
  console.log(`${greeting}, ${this.name}${punctuation}`);
}

const user = { name: 'Deeksha' };

// Basic binding
const boundHello = greet.myBind(user, 'Hello');
boundHello('!'); // "Hello, Deeksha!"

// Partial application
const boundHi = greet.myBind(user, 'Hi');
boundHi('.'); // "Hi, Deeksha."

// Constructor usage
function Person(name) {
  this.name = name;
}

const BoundPerson = Person.myBind(null, 'Default');
const p = new BoundPerson(); // `new` overrides the `null` context
console.log(p.name); // "Default"
```

## Quick Comparison

| Method  | Invokes Immediately | Argument Format    | Returns          |
|---------|--------------------|--------------------|-----------------|
| call()  | Yes                | Comma-separated    | Function result |
| apply() | Yes                | Array              | Function result |
| bind()  | No                 | Comma-separated    | New bound function |

## Common Interview Questions

- What is the difference between `call`, `apply`, and `bind`?
- How does `this` behave in arrow functions vs regular functions?
- Implement your own version of `bind()`.
- Why does `setTimeout` lose the `this` context?
- Explain implicit vs explicit binding.
