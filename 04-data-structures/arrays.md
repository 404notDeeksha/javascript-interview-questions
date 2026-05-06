# Arrays in JavaScript

Arrays in JavaScript are ordered collections of elements, where each element is accessed by its numeric index (starting from 0). Arrays can store values of any type, including numbers, strings, objects, or even other arrays. They are widely used for managing lists and collections of data in JavaScript.

## Array Methods

| Common Array Method | Description |
|----------------|   -----------------------------------------------------------------------------|
| length | Returns the number of elements in the array |
| toString() | Converts the array to a comma-separated string |
| at(index) | Returns the element at a given index |
| join() | Joins all elements into a string with a specified separator |
| pop() | Removes and returns the last element |
| push() | Adds one or more elements to the end |
| shift() | Removes and returns the first element |
| unshift() | Adds one or more elements to the beginning |
| concat() | Merges arrays and/or values into a new array |
| slice(start,end) | Returns a shallow copy of a portion of the array. start - inclusive. end - (optional, exclusive) |
| splice(start, deleteCount,elementsToAdd) | Adds/removes/replaces elements at a specified index. Mutates original Array. elementsToAdd - optional |
| copyWithin(target, start, end) | Copies part of the array to another location in the same array. Mutates original Array. |
| flat(depth) | Flattens nested arrays into a single array. depth - optional. Default Depth is 1. |
| forEach() | Executes a function for each array element. returns undefined |
| map() | Creates a new array by applying a function to each element. returns new array |
| filter() | Creates a new array with elements that pass a test. Returns new array |
| reduce() | Reduces the array to a single value by executing a function on each element |
| find() | Returns the first element that satisfies a test |
| findIndex() | Returns the index of the first element that satisfies a test |
| sort() | Sorts the elements of the array |
| reverse(callbackFn, initialVal) | Reverses the order of the elements |
| includes(value, fromIndex) | Checks if an array contains a certain value. |
| indexOf(value, fromIndex) | Returns the first index of a specified element |
| from() | Creates an array from an iterable or array-like object |
| entries() | Returns an iterator with key/value pairs |
| keys() | Returns an iterator with the keys (indexes) |

## Usage Examples

```js
let arr=['a','b','c'];
arr[-1];                      //undefined
arr.length;                   //3
new Array(arr.length);  //creates empty array with length = arr.length

//Creating String from Array
arr.toString();               //'a,b,c'
arr.at(2);                    //"c"
arr.join('-');                //"a-b-c"

// Adding, Removing elements
arr.pop();                    //"c"
arr.push('x');                //['a','b','x']
arr.shift();                  //"a"
arr.unshift("1");             //['1','b','x']
arr.concat(['e','f','g']);    //['1','b','x','e','f','g'] 
arr.slice(-2)        //['f','g']
arr.slice()          // ['1','b','x','e','f','g']- full shallow copy
arr.splice(1,2,'a','b');   //['1','a','b','e','f','g']
arr.copyWithin(0,1,3);        // ['a','b','b','e','f','g']

//Checks array for certain Value
arr.includes('e',4)        //false
array.indexOf('b')      //1
array.indexOf('b',2)    //2

//Nested Arr
arr=[1,2,3,[4,5,[6,[7]]]];
arr.flat();                   // [1,2,3,4,5,[6,[7]]]        
arr.flat(3);                  // [1,2,3,4,5,6,7] or arr.flat(Infinite)
arr.flat(Infinity);     //flatens infinely nested array.

//Iterating & Transforming : work on callback functions
arr=[1,2,3];
arr.forEach(num => console.log(num * 2));  //  2 4 6
arr.map(num => num * 2); // [2, 4, 6]
arr.filter(num => num % 2 === 0); // [2, 4]
arr.every(char => char === 0); // return boolean. all elements in arr must validate callback fn
arr.reduce((acc, curr) => acc + curr, 0); // 6
[5, 12, 18].find(num => num > 10); // 12
[5, 12, 8].findIndex(num => num > 10);        // 1
[4, 2, 10, 1].sort((a, b) => a - b);  // [1, 2, 4, 10]
[1, 2, 3].reverse()  // [3, 2, 1]

// Creating arrays
Array.from("hello");    // ['h', 'e', 'l', 'l', 'o']

const set = new Set([1, 2, 3]);
const arr = Array.from(set);
console.log(arr); // [1, 2, 3]

// Slice
let s = "ABC";

console.log(s.slice(0, 0)); // ""
console.log(s.slice(0, 1)); // "A"
console.log(s.slice(0, 2)); // "AB"
console.log(s.slice(1, 2)); // "B"
console.log(s.slice(1));    // "BC"
```