# What is the value of `console.log(+'meow')`? Explain your answer.

This will log `NaN`.

The operator `+` is known as the unary operator. When an element is prefixed by the unary operator, the JavaScript interpreter will try to convert that element into a number. If the conversion fails, this will result in `NaN`.

Under the hood, the unary operator attempts to call `valueOf()` and `toString()` to convert the element into a number.


For a deep dive on the unary operator and the conversion process for different types, I encourage you to read [The unary + operator](http://xkr.us/articles/javascript/unary-add/).