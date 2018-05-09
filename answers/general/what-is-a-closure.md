# What is a closure?

First, make sure to understand functional scope. Second, overall there seems to be a lack of consistency in regards to the definition of a closure so please be mindful when having intense conversations on this topic.

A closure is a function that retains access to variables of the context it was created in even after said function call has returned. 

Typically after a function has returned, variables that were created inside the context of that function are no longer accessible. Consider the following.

```javascript
var awFunc = function(first) {
  var someFunc = function(second) {
    return (first + second)
  }

  return someFunc('some')
}

var someNewFunc = awFunc('awe') // returns awesome
someNewFunc() // Uncaught ReferenceError

// Let's try to access the variables first and second
first // Uncaught ReferenceError
second // Uncaught ReferenceError

```

However we can refactor a little and come up with the following code

```javascript
var awFunc = function(first) {
  var someFunc = function(second) {
    return (first + second)
  }

  return someFunc // notice function is not invoked
}

var someMoreFunc = awFunc('awe') // At this point awFunc has finished running

// We can wait a long time right here if we want

someMoreFunc('somer') // returns awesomer
// I still have access to variables of awFunc even after it's finished running
```

So one obvious advantage is to allow for separation of concerns when writing code. This become extremely useful when considering asynchronous code.

Related topic includes [currying](../bestpractices/what-is-currying.md).


