# Why is my import statement not working in the browser?

Let's consider this code:

```
import React from 'react';

class HelloWorld extends React.Component {
  render() {
    return <p>Hello, world!</p>;
  }
}
export default HelloWorld;
```
We ran `npm install`, React is definitely included in our `package.json` and we're using Babel to transpile our code. Can you tell what's going wrong? Explain the bug and suggest a solution.

Can you think of a reason? The answer is quite simple, you can't use `import/export` statements in the browser.

Let's delve a bit deeper on why ES6 `import/export` statements don't work in the browser even though you're using Babel.
A common mistake is to think Babel is enough to handle this issue. Babel simply transpiles our code from ES6 to ES5 syntax, so it can be compatible with all browsers.

So in this case, `import/export` are transpiled by Babel to their CommonJS `require'/module.exports` equivalent.

In order to run client-side `import` statements, you'll need to use tools like [Webpack](https://webpack.github.io/)or [Browserify](http://browserify.org/).

You can also directly include the libraries/modules in your `index.html`

```
  <script src="node_modules/react/dist/react.js"></script>
  <script src="node_modules/react-dom/dist/react-dom.js"></script>
```

