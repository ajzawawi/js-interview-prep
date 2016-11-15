# What is function hoisting? Provide some examples where it can be good or bad.

Function (and also variable) hoisting is when a function (or variable) is available before it's actual declaration statement.

Consider the following code.

```javascript
// returns a is not defined - reference error
console.log(a)
```

```javascript
// returns undefined
console.log(a)
var a = "hello"
console.log(a)
````

Behind the scenes 'var a' is hoisted to the top. It is not declared, and so remains undefined, but no longer has a reference error.

Similarly, if a function is declared via functional declaration (using the keyword function) it is hoisted to the top. (However since the syntax of function delcaration has no assignment, the body of the function is hoisted.)

Compare variable vs function declaration.

```javascript
// foo exists indepedently from bar
var foo = 'bar'
// functoin foo exists with bar - not separated
function foo() {
  return 'bar'
}
```

So in this case the function can be invoked before it's function declaration statement. Observe below.

```javascript
// returns reference error - hard crash
console.log(foo())
```

```javascript
// returns 9
console.log(foo())
function foo() {
  return 9
}
```

This does not work for function expressions (assigning to a variable)

```javascript
// returns foo is not a function
console.log(foo())
var foo = function() {
  return 9
}
```

It would seem functional declaration can save us in certain situation.

However, depending on the scope it is possible to overwrite function that you may not intend to, resulting in chaos. See below.

```javascript
for (var n = 0; n < 1; n++) {
  // I invote giveBack accidentally ahead of declaring it
  // Would expect it to return error
  // In fact returns 1
  console.log(giveBack())
  var giveBack = function() {
    return 2
  }
}

// this get hoisted
function giveBack() {return 1}
```

While the example is rather benign, it is easy to see how this may result in an ongoing error which is not detected


