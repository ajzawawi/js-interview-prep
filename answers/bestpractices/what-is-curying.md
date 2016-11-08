# What is currying? What are some examples?

Currying is an over powered method that lets you make thirteen three points in a single game.

## Seriously, what is currying?

Currying is when you partial invoke a function, but not with all of it's argument with the purpose of returning it as  function that can be supplied its missing arguments later.

Consider the following.

```javascript
// es6!!
var add = (a, b) => {
  return a + b
}

// invoked add function partially with c and 2
var add2 = (c) => {
  return add(c, 2)
}

// returns 6
add2(4)
```

Currying lets you create library of easily configured functions and also helps with keeping code D.R.Y.