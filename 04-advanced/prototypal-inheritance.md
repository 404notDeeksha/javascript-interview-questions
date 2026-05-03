# Prototype & Prototypal Inheritance

## What is a Prototype?

Every JavaScript object has a prototype, which is another object that it inherits properties and methods from. The prototype acts as a template object that other objects can inherit from. This is the foundation of JavaScript's inheritance model.

**e.g.:** Objects created with a constructor function inherit from that constructor's `prototype` property. Built-in types like `Array` and `Date` have their own prototypes (`Array.prototype`, `Date.prototype`), which in turn inherit from `Object.prototype`.

## What is Prototypal Inheritance?

It is the mechanism by which objects in JavaScript inherit properties and methods from other objects via their prototype chain. When you access a property or method on an object, JavaScript will look for it on the object itself. If it's not found, it will look up the prototype chain until it finds it or reaches the end (`Object.prototype`).

## Key Concepts

### Prototype Chain
- Every object has an internal link to another object called its **prototype** (`[[Prototype]]`)
- Property lookup: own property → prototype → prototype's prototype → ... → `null`
- Chain ends at `Object.prototype` (whose prototype is `null`)

### `prototype` vs `__proto__` vs `[[Prototype]]`
- `prototype` - property on **constructor functions** (sets `[[Prototype]]` for instances)
- `__proto__` - deprecated getter/setter for `[[Prototype]]`
- `[[Prototype]]` - internal link (accessed via `Object.getPrototypeOf()`)

## Creating Inheritance

```js
// 1. Object.create()
const parent = { greet() { return "Hi"; } };
const child = Object.create(parent);

// 2. Constructor function
function Person(name) { this.name = name; }
Person.prototype.sayHi = function() { return this.name; };
const p = new Person("Jay");

// 3. ES6 classes (syntactic sugar over prototypes)
class Animal { speak() { return "..."; } }
class Dog extends Animal {}

// 4. Direct object inheritance
const animal = { eats: true };
const rabbit = Object.create(animal);
console.log(rabbit.eats); // true (inherited from animal)
```

## Prototype Chaining

Prototype chaining is the process JavaScript uses to look up properties on an object. When you access a property, JS traverses the chain of prototypes until it finds the property or reaches the end.

### How Property Lookup Works

```js
function Animal(name) {
  this.name = name;
}
Animal.prototype.speak = function() {
  return `${this.name} makes a sound`;
};

function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;
Dog.prototype.bark = function() {
  return `${this.name} barks!`;
};

const dog = new Dog("Rex", "Labrador");

// Lookup chain:
// dog → Dog.prototype → Animal.prototype → Object.prototype → null

dog.bark();     // Found on Dog.prototype
dog.speak();    // Found on Animal.prototype (walks up the chain)
dog.name;       // Found on dog itself (own property)
dog.toString(); // Found on Object.prototype (top of chain)
dog.unknown;    // undefined (reached end of chain)
```

### Building the Chain

```js
// Step 1: Base object
const vehicle = { type: "vehicle", move() { return "moving..."; } };

// Step 2: First level
const car = Object.create(vehicle);
car.wheels = 4;

// Step 3: Second level
const sportsCar = Object.create(car);
sportsCar.speed = 200;

// Chain: sportsCar → car → vehicle → Object.prototype → null
sportsCar.wheels; // 4 (from car)
sportsCar.move(); // "moving..." (from vehicle)
```

### Key Rules

1. **Reads traverse the chain** - accessing properties walks up prototypes
2. **Writes are always on the object itself** - setting a property creates it on the target object, never modifies the prototype
3. **Shadowing** - setting a property with the same name as an inherited one creates an own property that "shadows" the inherited one
4. **Performance** - long chains slow down property lookups; accessing properties far up the chain is slower

### Shadowing Example

```js
const parent = { name: "Parent", greet() { return `Hi from ${this.name}`; } };
const child = Object.create(parent);

console.log(child.name);        // "Parent" (inherited)
console.log("name" in child);   // true (found in chain)
child.hasOwnProperty("name");   // false (not own)

child.name = "Child";           // Creates own property (shadows)
console.log(child.name);        // "Child" (own property)
console.log(parent.name);       // "Parent" (unchanged)

delete child.name;              // Removes own property
console.log(child.name);        // "Parent" (falls back to prototype)
```

### Chain Visualization

```
dog (instance)
  ↓ [[Prototype]]
Dog.prototype
  ↓ [[Prototype]]
Animal.prototype
  ↓ [[Prototype]]
Object.prototype
  ↓ [[Prototype]]
null (end of chain)
```

### Checking the Chain

```js
const a = {};
const b = Object.create(a);
const c = Object.create(b);

Object.getPrototypeOf(b) === a;  // true
a.isPrototypeOf(c);              // true
c instanceof Object;             // true
```

## Important Methods

| Method | Description |
|--------|-------------|
| `Object.create(proto)` | Creates object with specified prototype |
| `Object.getPrototypeOf(obj)` | Returns `[[Prototype]]` |
| `Object.setPrototypeOf(obj, proto)` | Sets `[[Prototype]]` |
| `obj.hasOwnProperty(prop)` | Checks own property (not inherited) |
| `prop in obj` | Checks own + inherited properties |
| `obj instanceof Constructor` | Checks prototype chain |

## Key Points

1. Objects can inherit directly from other objects
2. The prototype chain allows for shared behavior and code reuse
3. Prototypal inheritance can be implemented using `Object.create()`, constructor functions, or classes
4. **Dynamic** - changes to prototype reflect on all inheriting objects
5. All built-in types inherit from `Object.prototype`

---

## Most Asked Interview Questions

### Q1: What is the difference between `prototype` and `__proto__`?

```js
function Person() {}
const p = new Person();

// p.__proto__ === Person.prototype  (true)
// __proto__ is the actual object used as prototype
// prototype is a property of the constructor function
```

**Answer:** `prototype` is a property on constructor functions that defines what `__proto__` will be for instances. `__proto__` is the actual internal link on an object to its prototype.

---

### Q2: What is the output?

```js
function A() {}
function B() {}
A.prototype = Object.create(B.prototype);
const a = new A();

console.log(a instanceof B);
console.log(a instanceof A);
console.log(a instanceof Object);
```

**Output:** `true`, `true`, `true`

**Why:** `instanceof` checks the prototype chain. `a.__proto__` → `A.prototype` → `B.prototype` → `Object.prototype` → `null`.

---

### Q3: How does `Object.create(null)` differ from `{}`?

```js
const obj1 = {};
const obj2 = Object.create(null);

console.log(obj1.toString); // function (inherited from Object.prototype)
console.log(obj2.toString); // undefined
```

**Answer:** `Object.create(null)` creates an object with **no prototype** at all. It doesn't inherit `toString`, `hasOwnProperty`, etc. Useful for pure dictionaries/maps.

---

### Q4: Implement inheritance without `class` keyword

```js
function Animal(name) {
  this.name = name;
}
Animal.prototype.speak = function() {
  return `${this.name} makes a sound`;
};

function Dog(name, breed) {
  Animal.call(this, name); // call parent constructor
  this.breed = breed;
}
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;
Dog.prototype.bark = function() {
  return `${this.name} barks!`;
};

const d = new Dog("Rex", "Labrador");
d.speak(); // "Rex makes a sound"
d.bark();  // "Rex barks!"
```

---

### Q5: What is prototypal vs classical inheritance?

| Prototypal (JS) | Classical (Java/C++) |
|-----------------|---------------------|
| Objects inherit from objects | Classes inherit from classes |
| Runtime composition | Compile-time blueprint |
| Flexible, dynamic | Rigid hierarchy |
| No classes needed (ES6 class is sugar) | Requires classes |

---

### Q6: Why avoid modifying `Object.prototype`?

```js
Object.prototype.foo = "bar";

const obj = {};
console.log(obj.foo); // "bar" — now on EVERY object!

for (let key in obj) {
  console.log(key); // "foo" appears in all for...in loops
}
```

**Answer:** It pollutes all objects, breaks `for...in` loops, and can conflict with future JS additions.

---

### Q7: What does this output and why?

```js
const obj = { a: 1 };
Object.setPrototypeOf(obj, { b: 2 });
Object.setPrototypeOf(Object.getPrototypeOf(obj), { c: 3 });

console.log(obj.a); // ?
console.log(obj.b); // ?
console.log(obj.c); // ?
```

**Output:** `1`, `2`, `3`

**Why:** Chain is `obj` → `{b:2}` → `{c:3}` → `Object.prototype` → `null`. All properties are accessible via the chain.

---

### Q8: How to check if a property is own vs inherited?

```js
const parent = { inherited: true };
const child = Object.create(parent);
child.own = true;

console.log(child.hasOwnProperty("own"));       // true
console.log(child.hasOwnProperty("inherited")); // false
console.log("inherited" in child);              // true
console.log(Object.hasOwn(child, "own"));       // true (ES2022)
```

---

### Q9: Why is `Dog.prototype.constructor = Dog` needed?

```js
function Animal() {}
function Dog() {}

Dog.prototype = Object.create(Animal.prototype);
// Dog.prototype.constructor is now Animal (broken!)

Dog.prototype.constructor = Dog; // fix it
const d = new Dog();
console.log(d.constructor === Dog); // true (after fix)
```

**Answer:** `Object.create(Animal.prototype)` makes `Dog.prototype.constructor` point to `Animal`. Resetting it ensures instances reference the correct constructor.

---

### Q10: How do ES6 classes work under the hood?

```js
class Animal {
  constructor(name) { this.name = name; }
  speak() { return "..."; }
}

// Equivalent to:
function Animal(name) { this.name = name; }
Animal.prototype.speak = function() { return "..."; };

class Dog extends Animal {
  bark() { return "woof"; }
}

// Equivalent to:
function Dog(name) { super(name); }
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;
Dog.prototype.bark = function() { return "woof"; };
```

**Answer:** ES6 `class` is **syntactic sugar** over prototypal inheritance. It uses the same prototype chain mechanism.
