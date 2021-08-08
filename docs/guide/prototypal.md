# More on Prototypes 

## Prototype Chain
Each object has a private property which holds a link to another object called its prototype. That prototype object has a prototype of its own, and so on until an object is reached with null as its prototype

## Prototypal Inheritance
Prototypal Inheritance is method by which one object can inherit properties from another object

```js

const car = {
  make: 'suzuki'
  model: 'alto'
}

const car2 = {}
// not recommended
car2.__proto__ = car

car2.make // suzuki

```

Inheritance eg: 2

```js
function Vehicle(make) {
  this.make = make;
}

Vehicle.prototype.getModel = function() {
  console.log(`${this.make} ${this.model}`)
}

Vehicle.prototype.honk = function() {
  console.log(`honk!! honk!!`)
}

function Car(make, model) {
  // Car inherits properties of Vehicle
  Vehicle.call(this, make)
  this.model = model;
}

// Inherit all functionalities of Vehicle
Car.prototype = Object.create(Vehicle.prototype)

// Set constructor to its own, else created objects will have constructor as Vehicle
Car.prototype.constructor = Car

function Bike(make, model) {
  // Bike inherits properties of Vehicle
  Vehicle.call(this, make)
  this.model = model;
  this.honk = function() {
   console.log(`beep!! beep!!`)
  }
}


// Inherit all functionalities of Vehicle
Bike.prototype = Object.create(Vehicle.prototype)
Bike.prototype.constructor = Bike

const suzuki = new Car('suzuki', 'alto')
const yamaha = new Bike('Yamaha', 'R15')

// Does not have its own honk() will default to inherited value of vehicle
suzuki.honk() // honk!! honk!!

// Will use its own honk() function
yamaha.honk() // beep!! beep!!

```

### Prototype implementations

Few examples for implementing [own prototypes](/guide/prototypeimp)

#### References: 

- [Inheritence and Prototype Chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [Prototypal Inheritance - Akshay Saini](https://www.youtube.com/watch?v=wstwjQ1yqWQ&ab_channel=AkshaySaini)
- [Prototype Chain Explained](https://chamikakasun.medium.com/javascript-prototype-and-prototype-chain-explained-fdc2ec17dd04)