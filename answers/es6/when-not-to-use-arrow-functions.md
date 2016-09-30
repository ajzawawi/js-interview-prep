# Arrow functions are cool in ES6. When should you NOT use arrow functions. Name three or more cases.

Arrow functions are neat but are not suitable for all use cases. For those who are ready to get rid of `function` and move on to arrow functions, it's time to examine a simple scenario where the arrow function would complicate your logic.

## Event Handlers

Let's look at this example, we have a link on our page with an id of `myLink`. Every time you hover over this link, a CSS class `highlight` is toggled and the text is highlighted.

```

var myLink = document.getElementById('myLink');

myLink.addEventListener('mouseenter', function(){
  this.classList.toggle('highlight');
   console.log(this.classList);
});

```
This logs `highlight`.

Using ES5 syntax, this works as expected. Now let's try that in ES6 using arrow functions:

```
const myLink = document.getElementById('myLink');

myLink.addEventListener('mouseenter', () => {
  this.classList.toggle('hightlight');
   console.log(this.classList);
});

```

This logs `TypeError: Cannot read property 'classList' of undefined`.

Womp womp. What's going on here? If you try to console log the value of this,
you'll get `window`. The `window` does not have a `classList` and your event
handler doesn't work as it should.

For a deep dive on different scenarios, I encourage you to read [Wes Bos's post on When Not to Use an Arrow Function](http://wesbos.com/arrow-function-no-no/
).

If you're not sure whether an arrow function is appropriate, [Kyle Simpson](https://github.com/getify/You-Dont-Know-JS/blob/master/es6%20%26%20beyond/ch2.md) provides us with this awesome chart:

![Arrow Functions Visual Aid](https://github.com/getify/You-Dont-Know-JS/raw/master/es6%20%26%20beyond/fig1.png)



