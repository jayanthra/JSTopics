# Debounce and throttle

Debounce and throttle are two rate limiting techniques used to limit the number of times a function is called over a period of time

## Debounce

Function is called only when time difference between two actions greater than set time
 
``` js
    let debounce = function (fn, delay) {
      let timer
      return function () {
        let context = this
        let args = arguments
        clearTimeout(timer)
        timer = setTimeout(() => {
          fn.apply(context, args)
        }, delay)
      }
    }
```

### Debounce demo
<p class="codepen" data-height="368" data-theme-id="dark" data-default-tab="result" data-user="jayanthracharya-the-animator" data-slug-hash="MWprKQe" style="height: 368px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Debounce">
  <span>See the Pen <a href="https://codepen.io/jayanthracharya-the-animator/pen/MWprKQe">
  Debounce</a> by Jayanth (<a href="https://codepen.io/jayanthracharya-the-animator">@jayanthracharya-the-animator</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

## Throttle

Function is called only once during between each specified time period

```js
let throttle = function(fn, limit) {
  let isCalled = false
  return function() {
    if (!isCalled) {
      let context = this
      let args = arguments

      fn.apply(context, args);
      isCalled = true

      setTimeout(() => {
        isCalled = false
      }, limit)
    }
  }
}
```

### Throttle demo

<p class="codepen" data-height="367" data-theme-id="dark" data-default-tab="result" data-user="jayanthracharya-the-animator" data-slug-hash="KKWZVGz" style="height: 367px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Throttle">
  <span>See the Pen <a href="https://codepen.io/jayanthracharya-the-animator/pen/KKWZVGz">
  Throttle</a> by Jayanth (<a href="https://codepen.io/jayanthracharya-the-animator">@jayanthracharya-the-animator</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

#### References:

- [Akshay Saini](https://www.youtube.com/watch?v=tJhA0DrH5co)
- [CSS-TRICKS](https://css-tricks.com/debouncing-throttling-explained-examples/)
