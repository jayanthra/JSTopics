# Closures

A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the `lexical environment`). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.


```js
function car() {
  const name = 'Suzuki';
  function displayName() {
    console.log(name)
  }
  return displayName;
}

var printCar = car();
printCar(); // Suzuki

```


### A multiplier function 

```js
function multiplier(x) {
  return function(y) {
    return x * y;
  };
}

var doubler = multiplier(2);
var tripler = multiplier(3);

console.log(doubler(2));  // 4
console.log(doubler(6)); // 12
console.log(tripler(3)); // 9
```

In this example, we have defined a function multiplier(x), that takes a single argument x, and returns a new function. The function it returns takes a single argument y, and returns the multiplication of x and y.

#### Practical uses of closures
- [Rate limiting : Debounce / throttle](/guide/ratelimiting)
- [Memoization](https://scotch.io/tutorials/understanding-memoization-in-javascript)
- [Currying](/guide/currying)

References:
- [MDN Web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)