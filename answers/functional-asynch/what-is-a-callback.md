# What is a callback?

In short, a callback is a function that is passed as an argument to another function. Consider the example below.

```javascript
var a = [1, 2, 3]

// console logs 1, 2, 3
// not this does not return anything
a.map(function(item) {console.log(item)})
```

Observe that we are passing the function (in this case an anonymous function) as the argument to map. This function is the callback.

## Asynchronously

More importantly, callbacks are regularly used with in asynchronous functions. This is a typical practice to extract some result when we are waiting for some action to come back before proceeding. A simple example exists below.

```javascripts

var asyncExample = function(cb) {
  setTimeout(function() {
    cb()
  }, 5000)
}

var printSomething = function() {console.log('something')}

asyncExample(printSomething) // console logs 'something' after 5000ms
```

This is especially common when dealing with ajax calls or reading/writing actions.

## Other notes

The context of a function can and will change when passed in as a callback. With that said, it means if a function or method references 'this' it will be necessary to use call/apply when trying to invoke that function in a callback.




