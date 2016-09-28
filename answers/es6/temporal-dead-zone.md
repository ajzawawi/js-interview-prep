# What is the Temporal Dead Zone?

To understand the concept of Temporal Dead Zone (TDZ), let's look at this familiar ES5 code:

```
console.log(language);
var language = 'JavaScript';

```

This will log `undefined`.

In ES5, all variable declarations are processed before any code is executed.
Known as `hoisting`, all `var` declarations appear to be moved to the top. In this example, the variable language
is hoisted and declared, however; it has not been assigned the value of `JavaScript` yet.

Now let's look at the same code using ES6 syntax:

```
console.log(language);
let language = 'JavaScript';

```
This will throw a `ReferenceError`.

A common mistake is to assume that the `let/const` were not hoisted. The short answer is that `let/const` declarations are hoisted, but they will throw errors when you try to access them before a value is initialized.

How will this affect your code? If you had `if-statements` checking if the variable is currently set to `undefined`, this will require your attention and a revision of the app's logic.

For a deep dive on why `let/const` are different, I encourage you to read [Fabrício S. Matté's post on TDZ](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified/).

