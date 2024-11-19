# Callbacks
A callback is a function passed as an argument to another function, to be "called back" (executed) later in the program, often once an asynchronous operation has completed.

A basic function with a callback can look like this:
```js
function greet(name, callback) {
    console.log(`Hello, ${name}!`);
    callback();
}

function sayGoodbye() {
    console.log("Goodbye!");
}

// Calling greet and passing sayGoodbye as a callback
greet("Alice", sayGoodbye);

// Can also be called like this of course
greet("Alice", () => console.log("Goodbye!"));
```

## When to Avoid
Callbacks are cool but not suited for every use. There are a couple things that should be avoided when possible.

### Callback Hell
It's horrible.
```js
doSomething(() => {
    doSomethingElse(() => {
        doAnotherThing(() => {
            console.log("Done!");
        });
    });
});
```
### Promises/`async`/`await`
Most of the time its easier to use promises or something like `async`/`await`.
