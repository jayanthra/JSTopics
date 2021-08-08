# Array cheet sheet

### slice()

Returns a copy of part of array, while original array is not modified

```js
[ 1, 2, 3, 4 ].slice(1) // [2, 3, 4]
[ 1, 2, 3, 4 ].slice(1, 3) // [ 2, 3 ]
[ 1, 2, 3, 4, 5, 6, 7 ].slice(3,6)  // [3, 5, 6]
// syntax
arr.slice([begin[, end]])

// begin included, end excluded
```

### splice()

Changes contents of array by removing, replacing and/or adding elements

```js
const arr = [ 1, 2, 3, 4, 5 ]
// from index 1 remove 2 items and replace with "a"
arr.splice(1, 2, 'a') // returns [ 2, 3 ] // arr is [ 1, "a", 4, 5]

// from index 1 remove 0 items and replace with "a"
arr.splice(1, 0, 'a') // returns [ ] // arr is [ 1, "a", 2, 3, 4, 5]

// from index 1 remove 0 items and replace with nothing
arr.splice(1, 1) // returns [1] // arr is [1, 3, 4, 5]

// syntax
let arrDeletedItems = array.splice(start[, deleteCount[, item1[, item2[, ...]]]])
```

### filter()

```js
var meals = ['breakfast', 'lunch', 'dinner', 'supper'];

meals.filter(function(item) {
  return item !== 'breakfast';
});

// ['lunch', 'dinner', 'supper'];
```

### some()

Checks whether at least one element in array passes the test

```js
var meals = ['breakfast', 'lunch', 'dinner', 'supper'];

meals.some(function(item){ return item === 'lunch';});
// true

meals.some(function(item){ return item === 'burgers!!';});
// false
```

#### More:

[Array Cheat Sheet](https://gist.github.com/ourmaninamsterdam/1be9a5590c9cf4a0ab42)