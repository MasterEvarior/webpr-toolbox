# Functions in JavaScript

JavaScript function initially look a lot like Java functions, just without the type system.

```js
function myCoolFunction(a, b){
    return a + b;
};

myCoolFunction(1, 2) // evaluates to 3
```

But they can also be written in other ways, because they are essentially just references to a "function" object.

```js
// Same as above
const myCoolFunction => (a,b) => { return a + b; };

// With no arguments, always returns 1
const noArgs => () => { 1; };
```

Those ways of writing functions also enables that we can write functions in JS, that return something without using the `return` statement.

```js
// This always return 1
const return = () => 1;

// BUT THIS RETURN UNDEFINED! DONT DO THIS!
function noReturn()     { 1; }
const noReturn2 = () => { 1; }; // noch nicht das, was wir brauchen
```

As mention previously, functions are essentially just an object. This means we can also define functions as variables or even put them into an array.
```js
function fun1(){ return 1; };
const myfun = fun1;
const funs = [null, undefined, fun1];
        
// The function can then be called like this
funs[1]()
```

That also allows us to pass functions as arguments to other functions. Kinda like Lambda expressions in Java.
```js
function doit(whatToDo) {
    return function bla(arg) { 
        return whatToDo(arg); 
    }
}

doit(fun1)();

// Same thing but written differently
const doit2 = callme => arg => callme(arg) ;
doit2(fun1)()
```