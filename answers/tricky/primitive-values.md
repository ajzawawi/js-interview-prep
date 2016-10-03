# What does `3 instanceof Number` evaluate to? True or false? Explain your answer.

It will evaluate to `false`.

Let's look at this in depth:

```
var num1 = 3;
var num2 = new Number(3);

console.log(num1 instanceof Number); // false
console.log(3 instanceof Number); // false
console.log(num2 instanceof Number); // true

```

What's the difference between `num1` and `num2`. In this case, num1 is a primitive or simple value. `num2` is a complex value. Let's log the type of each variable.

```
console.log(typeof num1); // "number"
console.log(typeof num2); // "object"

```

So in the question, we use `instanceof` which is basically `Constructor.prototype.isPrototype(value)`.
The number `3` is a primitive value and therefore not a product of the `Number` constructor call.

For a deep dive on primitive types and reference types, I encourage you to read [Angus Croll's The Secret Life of JavaScript Primitives](https://javascriptweblog.wordpress.com/2010/09/27/the-secret-life-of-javascript-primitives/).



