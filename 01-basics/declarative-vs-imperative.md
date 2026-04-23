# Declarative vs Imperative Programming

## Imperative

This style of programming gives step by step instructions for how to achieve goals. main focus is on sequence of operations & control flow. eg: C, Python, Java, DSA use this approach.

```js
let results = [];
for (let num of collection) {
    if (num % 2 !== 0) {
    results.push(num);
    }
}
```

## Declarative

This style of programming focuses on desired outcome & letting system decide how to do it. eg: SQL, HTML, React's JSX use this format.

```js
let results = collection.filter(num => num % 2 !== 0);
```