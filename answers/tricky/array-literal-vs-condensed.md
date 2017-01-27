# What is the difference between an array literal vs a condensed array?

Sometimes a trick question, but if they asked it they are probably fishing for something. 

First off, what does this all mean?

## Array literal

An array literal is our usual way of declaring and array.

```javascript
var a = [1, 2, 3] // a = [1, 2, 3]
````

# Condensed array

A condensed array is instatiated using the Array constructor.

```javascript
var b = new Array(1, 2, 3) // b = [1, 2, 3]
```

# No Difference?

So in this case there is no difference. We've used both of them nicely and ended up with the same result. However the condensed array approach has a few other intricacies.

Consider the following...

```javascript
var c = new Array(10) // c = [ , , , , , , , , , ]
```

This can save some time if you want to create an arry with multiple undefined values.

But it's not all good news.

Consider the following...

```javascript
var d = [4, 5, , 7, 8] // d = [4, 5, undefined, 7, 8]

var e = new Array(4, 5, , 7, 8 ) // Syntax error
```

So, there is a difference depending on how you use it.
