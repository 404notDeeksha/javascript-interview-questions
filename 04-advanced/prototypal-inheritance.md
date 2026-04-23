# Prototypal Inheritance

It is the mechanism by which objects in JavaScript inherit properties and methods from other objects via their prototype chain. When you access a property or method on an object, JavaScript will look for it on the object itself. If it's not found, it will look up the prototype chain until it finds it or reaches the end (Object.prototype).

## Key Points

1. Objects can inherit directly from other objects.
2. The prototype chain allows for shared behavior and code reuse.
3. Prototypal inheritance can be implemented using Object.create(), constructor functions, or the __proto__ property.

```js
const animal = { eats: true };
const rabbit = Object.create(animal);
console.log(rabbit.eats); // true (inherited from animal)
```