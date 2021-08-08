# call, apply, bind

## bind()

The bind() method creates a new function that, when called, has its <mark>this</mark> keyword set to the provided value

```js
const maruti = {
  make: 'Maruti',
  model: '800',
};

const suzuki = {
  make: 'Suzuki',
  model: 'Alto',
};

const startCar = function() {
  console.log(`${this.make} ${this.model} STARTED!!`);
};

const startSuzuki = startCar.bind(suzuki);
const startMaruti = startCar.bind(maruthi);

startSuzuki(); // Suzuki Alto STARTED!!
startMaruti(); // Maruti 800 STARTED!!

```

## call()

The call() method calls a function with a given <mark>this</mark> value and arguments provided individually.

Unlike bind() , the call() method 

- Can accpet additional arguments
- Executes the function right away.
- Does not make a copy of the function it is being called on.

## apply()

Similar to call but takes in array as arguments whereas call() takes comma separated values as arguments

```js

const maruthi = {
  make: 'Maruthi',
  model: '800',
};

const describeCar = function(color, tint) {
  console.log(`${this.make} ${this.model} is ${color}, with ${tint} tint`);
};

describeCar.call(maruthi, 'red', 'blue')
describeCar.apply(maruthi, ['red', 'blue']) 
// Maruthi 800 is red, with blue tint

```

::: tip DIFFERENCE
  `apply()` : A[rray]PPLY <br />
  `call()`  : C[omma]ALL
:::

References:
- [MDN Web docs bind()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)
- [MDN Web docs call()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)
- [MDN Web docs apply()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)
