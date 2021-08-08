# Currying

Currying is a process where we transform a function with multiple arguments into sequence of nesting functions that take one argument at a time

eg: transforming function from callable as f(a, b, c) into callable as f(a)(b)(c) is currying

Currying doesn’t call a function. It just transforms it.

```js
function curry(f) { // curry(f) does the currying transform
  return function(a) {
    return function(b) {
      return f(a, b);
    };
  };
}

// usage
function sum(a, b) {
  return a + b;
}

let curriedSum = curry(sum);

console.log(curriedSum(1)(2)); // 3
```

#### Advanced Currying

```js
function curry(func) {
  return function curried(...args) {
    if (args.length >= func.length) {
      return func.apply(this, args);
    } else {
      return function(...args2) {
        return curried.apply(this, args.concat(args2));
      }
    }
  };
}

function sum(a, b, c) {
  return a + b + c;
}

let curriedSum = curry(sum);

console.log(curriedSum(1, 2, 3)); // 6, still callable normally
console.log(curriedSum(1)(2,3)); // 6, currying of 1st arg
console.log(curriedSum(1)(2)(3)); // 6, full currying
```


#### References:

[JavascriptInfo](https://javascript.info/currying-partials)