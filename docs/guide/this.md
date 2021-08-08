# this

`this` keyword in a function refers to the execution context for that particular call
value of `this` is determined how the function is invoked

There are 4 ways to invoke a function, in order of precedence

- `new` binding
- Explicit binding
- Implicit binding
- Default binding

### new binding

The function is invoked with `this` references an empty object
Javascript creates an empty `this = {}` in `Car` function

```js

// Constructor function
function Car(make) {
  // this = {}
  console.log(this) // Car {}
  this.make = make
}

const car1 = new Car('Maruti')
const car2 = new Car('Suzuki')
```
### Explicit binding

```js
const car = {
  make: 'Maruti'
}

const printBrand = function() {
  console.log(`Car brand is ${this.make}`)
}

printBrand.call(car); // Car brand is Maruti
```

read more ways to implement explicit binding using [call/apply/bind](/guide/callapply)

### Implicit binding

```js
const car = {
  make: 'Maruti',
  printBrand: function() {
    console.log(`Car brand is ${this.make}`)
  }
}

car.printBrand() // Car brand is Maruti
```

when function is invoked with dot(.) notation, the `this` refers to the object left of dot, in this case it is the `car` object

### Default binding

Fallback if none of the others rules are matched

```js
const printBrand = function() {
  console.log(`Car brand is ${this.make}`)
}

printBrand() // Car brand is undefined 
```

Javascript with default to global scope and set `this` to window object

```js
var make = 'Suzuki'
const printBrand = function() {
  console.log(`Car brand is ${this.make}`)
}

printBrand() // Car brand is Suzuki  
```
`this.make` in window object is `Suzuki`


Reference: 
- [MDN Web docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)