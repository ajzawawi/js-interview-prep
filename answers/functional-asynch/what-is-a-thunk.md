# What is a thunk in Javascript?

A syncronous thunk is a function that has everything already needed to return a value, it does not require any arguments be passed in. In the case of an asynchronous thunk, it requires only a callback in order for it to return the value.

Consider the following examples.

```javascript
var str2arr = function(str) {
  return str.split('')
}

var thunkStr2arr = function() {
  return str2arr('hohoho')
}

thunkStr2arr() // returns [ 'h', 'o', 'h', 'o', 'h', 'o' ]


var str2arrAsync = function(str, cb) {
  setTimeout(function() {
    cb(str.split(''))
  }, 1000)
}

var thunkStr2arrAsync = function(cb) {
  return str2arrAsync('hahaha', cb)
}

thunkStr2arrAsync(console.log) // returns [ 'h', 'a', 'h', 'a', 'h', 'a' ]
```