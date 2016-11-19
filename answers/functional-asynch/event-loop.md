# What is the event loop in Javascript? How does this differ/compare to some other languages?

## Understanding a bit how Javascript differs from some other languages.

In order to understand the event loop in Javascript, it is good to understand the results first. Consider the following examples.

```javascript
var eatBeforeSwim = function(callback) {
  setTimeout(callback, 1000)
  console.log('Time for a swim!')
}

var eatPizza = function() {
  console.log('I ate some pizza!')
}

eatBeforeSwim(eatPizza)
// Logs 'Time for a swim!', after about 1000ms logs 'I ate some pizza!'
```

In Javascript, action that wait to return (such as setTimeout or AJAX calls, are non blocking). This means the code will continue to run while waiting for something to come back. This is often referred to as the asynchronous nature of Javascript. Compare this with a Ruby example below.

```ruby
def eat_before_swim(some_action) 
  sleep(1)
  puts (some_action)
  puts ('Time for a swim!')
end

eat_before_swim('I ate some pizza!')
// After 1s logs 'I ate some pizza!', then logs 'Time for a swim!
```

While the code is not equivalent, the concept to get across is that in Ruby the sleep action is blocking things from moving forward. Similar behavior is experienced with http requests. So the subsequent lines will not be evaluated and run until the previous line is complete.

## Event loop in Javascript

Now that we understand Javascript is asynchronous, we can look at the event loop. In essence, the event loop is responsible for how this asynchronous behavior happens. Before going further it is important to understand a few additional points about Javascript.

### Javascript is single threaded

This means Javascript will process each line of code after the previous line of code. We intentionally do not use the word run here. In order to evaluate when/how to run lines of code, Javascript keeps track of two things.

### Event Table (Hash) and Event Queue

When the Javascript engine comes across a line of code that needs to be run, it places the 'trigger' of that execution and the action of it in an event table. Later on, when the engine checks the event table, any events that have transpired, the corresponding action is moved into an event queue. Later on, when the engine checks the event queue, if there is an event there to execute it will do so. After executing, it will check the event table again to see if any new events have transpired.

Javascript is looping through this process over and over. (There may also be some additional processes but not part of the event loop discussion).

### Relating to callbacks

In the case of a callback, when the initial function is invoke (let's say setTimeout), the trigger-action pair of '1000ms in the future' and callback are added to the event table. Later on, when the Javascript engine checks the event table and '1000ms in the future' has transpired, it will add the callback ot the event queue.

In reality, the callback is executed the next time the Javascript engine checks the event queue. In fact it is possible this may not be right away, and so the actual timing of the callback being executed is not 1000ms. 

(Editor notes - needs picture probably)

## Closing notes

This explanation is intentionally broad as to provide a basic understanding. If there is further curiosity on this topic, it's suggested the reader do a deep dive into the topic. However for more roles it's unlikely a super indepth knowledge will be a requirement.

