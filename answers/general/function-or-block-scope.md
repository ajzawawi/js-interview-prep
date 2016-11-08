# Is JavaScript block-scoped or function scoped?

Short answer - Javascript is function scoped.

## What is block-scoped?

Block-scoped exists when a declared variable has inside a block of code (usually enclosed between curly backets) is only visible/accessible within that block of code. 

Consider the following.

var testFunc() {

  // var is defined in the this for loop block
  for (var n = 0; n < 10; n++) {
    var printed = n
  }

  // logs 10 - printed is defined outside of block
  console.log(printed)
}

Thus Javscript is function scoped.