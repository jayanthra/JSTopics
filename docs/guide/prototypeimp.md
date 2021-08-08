
# Own Prototype implementations

#### Bind

```js
Function.prototype.myBind = function(...obj) {
  const params = obj.slice(1)
  const bindingFunc = this
  return function() {
    bindingFunc.apply(obj[0], params)
  }
}
```

#### Map

```js
Array.prototype.myMap = function(fn) {
  const resultArray = [];
  let arr = this
  arr.forEach((item) => {
  	resultArray.push(fn(item));
  })
  return resultArray;
}
```

#### Filter

```js
Array.prototype.myFilter = function(fn) {
  const resultArray = [];
  let arr = this
  arr.forEach((item) => {
    if(fn(item))
  	  resultArray.push(item);
  })
  return resultArray;
}
```

#### Reduce

```js
Array.prototype.myReduce = function(fn, acc) {
  let arr = this
  if (!acc) {
    if (typeof arr[0] === "string") {
      acc = '';
    } else if (typeof arr[0] === "number") {
      acc = 0;
    }
  }

  arr.forEach((item) => {
    acc = fn(acc, item);
  })

  return acc;
}
```