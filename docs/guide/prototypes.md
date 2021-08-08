# Prototype

Prototypes are the mechanism by which JavaScript objects inherit features from one another.

## Lookback
check the following code

```js
function Car(make) {
  let car = {}
  car.make = make;
  car.checkBrand = function() {
    console.log(`Brand is ${this.make}`)
  }

  car.start = function() {
    console.log(`${this.make} started`)
  }

  car.stop = function() {
    console.log(`${this.make} stopped`)
  }

  return car
}

const suzuki = Car('Suzuki')
const maruti = Car('Maruti')

suzuki.start()
maruti.stop()
```

If there is a new Object of type `Bus` the functionalities of the vehicles (start, stop, checkBrand) need to be reused, this can be done by 

```js
const vehicleFunctions = {
  stop: function() {
    console.log(`${this.make} stopped`)
  },
  start: function() {
    console.log(`${this.make} started`)
  },
  checkBrand: function() {
    console.log(`Brand is ${this.make}`)
  }
} 

function Bus(make) {
  let bus = {}
  bus.make = make;
  bus.start = vehicleFunctions.start;
  bus.checkBrand = vehicleFunctions.checkBrand;
  return bus
}

function Car(make) {
  let car = {}
  car.make = make;
  car.start = vehicleFunctions.start;
  return car
}

// Further improvement
// using Object.create we have used all vehicle functionalities
function Bike(make) {
  let bike = Object.create(vehicleFunctions)
  bike.make = make;
  return bike
}


const suzuki = Car('Suzuki')
const tata = Bus('Tata')
const yamaha = Bike('Yamaha')

suzuki.start() // Suzuki started
tata.start() // tata started
yamaha.start() // Yamaha started
```
Now the vehicle functionalities has been reused and we have selected, using `Object.create` , when function is invoked, JS will check if the object had that function else it will use from `vehicleFunctions`


### Prototypes 

In Javascript every object has a property called prototype that references an object,
we can improve the previous code using prototype concept

```js

Bike.prototype.start = function() {
  console.log(`${this.make} started`)
}

Bike.prototype.stop = function() {
  console.log(`${this.make} stopped`)
}

function Bike(make) {
  let bike = Object.create(Bike.prototype)
  bike.make = make;
  return bike
}

const yamaha = Bike('Yamaha')
yamaha.start()
yamaha.stop()

```

Next improvement, `new` keyword and prototype

```js
Bike.prototype.start = function() {
  console.log(`${this.make} started`)
}

Bike.prototype.stop = function() {
  console.log(`${this.make} stopped`)
}

function Bike(make) {
  this.make = make;
}

const yamaha = new Bike('Yamaha')
const honda = new Bike('Honda')
yamaha.start() // Yamaha started
honda.stop() // Honda stopped

```

### Prototype implementations

Few examples for implemting [own prototypes](/guide/prototypeimp)

Reference

[MDN docs](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes)
