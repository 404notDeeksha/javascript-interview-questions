# reduce Method

```js
let arr=[1,2,3,4];
arr.reduce((acc, curr) => acc + curr, initialVal);    //10
```

acc: initialVal =  0;
reduce goes through each element, & acc = acc + curr

```js
curr=1; acc = 0 + 1
curr=2; acc = 1 + 2
curr=3; acc = 3 + 3
curr=4; acc = 6 + 4
acc=10; //returns
```

## Interview Questions

### Q: What is the default initial value of accumulator in reduce?
**A:** If no initial value is provided, the first element of the array becomes the initial accumulator value, and iteration starts from the second element.

```js
[1, 2, 3].reduce((acc, curr) => acc + curr); // 6
// acc starts as 1, iteration begins from index 1
```

### Q: What happens if reduce is called on an empty array without an initial value?
**A:** It throws a `TypeError: Reduce of empty array with no initial value`. Always provide an initial value when the array might be empty.

```js
[].reduce((acc, curr) => acc + curr, 0); // 0 (safe)
[].reduce((acc, curr) => acc + curr);     // TypeError
```

### Q: How to use reduce to flatten an array?
**A:** Use concat or spread operator inside reduce.

```js
const nested = [[1, 2], [3, 4], [5]];
const flat = nested.reduce((acc, curr) => acc.concat(curr), []);
// [1, 2, 3, 4, 5]
```

### Q: How to use reduce to group array elements?
**A:** Use an object as accumulator to group elements by a key.

```js
const people = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 },
  { name: 'Charlie', age: 25 }
];

const grouped = people.reduce((acc, person) => {
  const key = person.age;
  acc[key] = acc[key] || [];
  acc[key].push(person);
  return acc;
}, {});
// { 25: [{name:'Alice'},{name:'Charlie'}], 30: [{name:'Bob'}] }
```

### Q: Difference between reduce and map/filter?
**A:** `map` and `filter` always return arrays of same or smaller size. `reduce` can return any type (number, string, object, array) and transforms the array into a single accumulated value.