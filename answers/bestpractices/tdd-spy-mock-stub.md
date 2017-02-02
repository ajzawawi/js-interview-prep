# In TDD what is the difference between a spy, mock, and stub?

## What is TDD?

First off, TDD stands for test driven development. At a very broad level, it means requiremetns are set up as specific test cases prior to actually code writing. The purpose of writing new code is to past the established test.

[More info](https://en.wikipedia.org/wiki/Test-driven_development)

## So what is a spy, mock and/or stub?

There is some vagueness to this question, but it's used as a basis if you've actually understand TDD at a deeper level. Most of the answers in this readme are based on usage with Sinon. Terminology/use may vary with a different testing framework.

### What's a spy?

A spy is typically used to gather information about function calls. In essence, a spy can hijack a function and add additional properties that allow you observe other things about that function. For example, we can determine how many times a function was called and validate that against any expected behavior. It's possible we want to make sure an function for an AJAX call we implemented only runs once, we could use a spy to determine that.

### What's a stub?

A stub is a function that replaces another function completely. Instead of only hijacking and adding properties, it completed replaces the function. Stubs are useful when you want to guarantee a specific response. For example, our AJAX call needs to get a specific response, but it's possible the endpoint is not up and running, in this case we could use a stub.

### What's a mock?

Mocks are very similar to subs, but are primarily useful if you want to sub more than on function on a given object. Instead of replacing functions, you can mock an entire object.

