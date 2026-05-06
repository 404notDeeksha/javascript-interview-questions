# Indexed Collections in React

These are data structures where elements are stored and accessed using numerical indexes. In JavaScript (and therefore in React), the most common indexed collection is the array, which renders list of elements.

```js
const items = ["Apple", "Banana", "Cherry"];
return (
   <ul>
   {items.map((item, index) => (
      <li key={index}>{item}</li>
    ))}
   </ul>
);
```

> Unique key is to be used for each element when rendering lists.