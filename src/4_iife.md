# Immediatly Invoked Function Expression
An immediatly invoked function expression, short IIFE, are functions without names, that are executed immediatly.

JavaScript function initially look a lot like Java functions, just without the type system.  

You can achieve this by writting an empty lambda function and define this as a function:
```js
(() => {
    //do stuff
})()
```
Ok thats cool but how did we get here? If we do it step by step it gets a lot easier to understand:
```js
function foo(){} foo();
(function foot(){})(); //evluate directly, loose the function call
(function(){})() //loose the function name
(() => {})() //loose the keyword
```
Using IIFE can have a couple advantages:
- Encapsulates variables and their values which prevents pollution of (global) namespace
- Mimize risks of name collisions
