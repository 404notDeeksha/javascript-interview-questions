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