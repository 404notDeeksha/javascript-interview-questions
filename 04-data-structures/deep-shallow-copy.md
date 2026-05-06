# Deep & Shallow Copy + Copy by Reference

## Copy by Value (Primitives)

Primitive types (string, number, boolean, null, undefined, symbol, bigint) are stored directly in the variable. Assigning them creates a new copy.

```js
let a = 10;
let b = a;
b = 20;
console.log(a); // 10 (unchanged)
console.log(b); // 20
```

## Copy by Reference (Objects & Arrays)

Objects and arrays are stored in memory, and variables hold references (pointers) to that memory location. Assigning one variable to another copies the reference, not the value.

```js
let obj1 = { name: 'Alice' };
let obj2 = obj1;
obj2.name = 'Bob';
console.log(obj1.name); // 'Bob' (changed!)
console.log(obj2.name); // 'Bob'
// Both variables point to the same object in memory
```

## Shallow Copy

A shallow copy creates a new object/array, but nested objects are still shared by reference. Only the top-level properties are copied.

### Methods that create shallow copies

```js
const original = { name: 'Alice', address: { city: 'NYC' } };

// 1. Spread operator
const shallow1 = { ...original };

// 2. Object.assign()
const shallow2 = Object.assign({}, original);

// 3. Array methods (for arrays)
const arr = [1, [2, 3]];
const shallowArr1 = [...arr];
const shallowArr2 = arr.slice();
const shallowArr3 = Array.from(arr);

// Demonstration of shared nested reference
shallow1.address.city = 'LA';
console.log(original.address.city); // 'LA' (nested object still shared)
```

## Deep Copy

A deep copy creates a completely independent clone. All nested objects and arrays are recursively copied. Changes to the clone never affect the original.

### Methods to create deep copies

```js
const original = { name: 'Alice', address: { city: 'NYC' } };

// 1. structuredClone() (Modern, recommended)
const deep1 = structuredClone(original);

// 2. JSON.parse(JSON.stringify()) (Legacy, has limitations)
const deep2 = JSON.parse(JSON.stringify(original));

// 3. Manual recursive copy
function deepClone(obj) {
  if (obj === null || typeof obj !== 'object') return obj;
  if (Array.isArray(obj)) return obj.map(deepClone);
  return Object.fromEntries(
    Object.entries(obj).map(([key, value]) => [key, deepClone(value)])
  );
}
const deep3 = deepClone(original);

deep1.address.city = 'LA';
console.log(original.address.city); // 'NYC' (completely independent)
```

## Interview Questions

### Q: What is the difference between shallow and deep copy?
**A:** A **shallow copy** duplicates only the top level. Nested objects remain shared by reference. A **deep copy** recursively duplicates everything, creating a fully independent clone.

### Q: What are the limitations of JSON.parse(JSON.stringify()) for deep cloning?
**A:** 
1. Loses `undefined` values (they become `null` or are removed)
2. Cannot handle functions (they are removed)
3. Cannot handle `Date` objects (converted to strings)
4. Cannot handle `RegExp`, `Map`, `Set`, `Infinity`, `NaN`
5. Cannot handle circular references (throws error)
6. Loses prototype chain

```js
const obj = {
  fn: () => {},
  date: new Date(),
  undef: undefined,
  circular: null
};
obj.circular = obj;

JSON.parse(JSON.stringify(obj)); // TypeError: Circular structure
```

### Q: What is structuredClone() and why is it preferred?
**A:** `structuredClone()` is a modern built-in API that creates true deep copies. It handles `Date`, `RegExp`, `Map`, `Set`, `ArrayBuffer`, circular references, and more. Unlike JSON methods, it preserves data types correctly.

```js
const map = new Map([['key', 'value']]);
const cloned = structuredClone(map);
console.log(cloned instanceof Map); // true
```

### Q: Does the spread operator create a deep copy?
**A:** No, spread creates a **shallow copy**. Nested objects are still shared by reference.

```js
const original = { nested: { value: 1 } };
const copy = { ...original };
copy.nested.value = 2;
console.log(original.nested.value); // 2 (shared!)
```

### Q: How do you deep copy an array of primitives?
**A:** For arrays of primitives (no nested objects), spread, slice, or from all work fine since primitives are copied by value.

```js
const nums = [1, 2, 3];
const copy = [...nums];
copy[0] = 99;
console.log(nums); // [1, 2, 3] (unchanged)
```

### Q: What happens when you pass an object to a function?
**A:** Objects are passed by reference. Modifying the object inside the function affects the original.

```js
function updateUser(user) {
  user.name = 'Updated';
}

const user = { name: 'Alice' };
updateUser(user);
console.log(user.name); // 'Updated'
```

### Q: How to prevent mutation of objects passed to functions?
**A:** Create a shallow or deep copy before modifying, depending on the structure.

```js
function safeUpdate(user) {
  const copy = { ...user }; // or structuredClone(user) for deep
  copy.name = 'Updated';
  return copy;
}
```

### Q: When is shallow copy sufficient vs when do you need deep copy?
**A:** 
- **Shallow copy** is enough when: Object has only primitive values, or you intentionally want to share nested references
- **Deep copy** needed when: Object has nested objects/arrays that must be fully independent

### Q: How does Object.assign() work for copying?
**A:** `Object.assign()` copies enumerable own properties from source to target. It's a shallow copy.

```js
const source = { a: 1, b: { c: 2 } };
const target = Object.assign({}, source);
target.b.c = 99;
console.log(source.b.c); // 99 (nested still shared)
```
