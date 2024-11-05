# Type System
Because JavaScript has no compiler, types cannot be enforced by it. It can, however, be enforced by your IDE.

## Built in Types
JavaScript has a whole list of primitive builtin types:
- `Boolean`
- `Number`
- `String`
- `Object`
- `Null`
- `Undefined`
- `Function`
- `...`

It has also a couple of classes, that can be used the same way in JsDocs:
- `Array`
- `Date`
- `Error`
- `Map`
- `...`

## JsDoc
JsDoc looks very similiar to JavaDoc. It has, on account of the missing compiler, a couple more features though. It can not only document but also define the input/output types or define entire "custom types".

This is a very basic definition:
```javascript
/**
 * This is a basic description of a function.
 * @param { String } name - The name of the person.
 * @param { Number } age - The age of the person.
 * @returns { String } A greeting message.
 */
function greet(name) {
  return `Hello, ${name}! You are going to be ${age + 1} next year.`;
}
```

### Common Tags
There are a lot of tags in JsDoc. Here are the most frequently used listed, a couple of them have more infos further below.
- `@function` - Explicitly marks a block as a function, often for function expressions or anonymous functions.
- `@param` - Describes a function parameter.
- `@template` - Allows generic types, similar to TypeScript generics.
- `@returns` - Describes what the function returns.
- `@type` - Declares the type of a variable.
- `@typedef` - Creates a custom type, like an object structure.
- `@property` - Defines properties in a custom type.
- `@constructor` - Indicates that a function is intended to be used as a constructor (for creating instances of an object).
- `@callback` - Defines a function signature expected to be used as a callback type, specifying its parameters and return type.

### Define Data Types
**Union type:**
This is useful if the parameter can have multiple types.
```javascript
/**
 * Get a string to describe the age of a person
 * @param { Number | String } age - The age of the person.
 * @returns { String } A greeting message.
 */
function age(age) {
  return `You are ${age} year(s) old!`;
}
```
**Intersection type:** 
Here the type must be a person who is also cool. This helps enact even more specific type checking.
```javascript
/**
 * Log how cool a person is
 * @param { Person & Cool } person - A cool person.
 */
function cool(person) {
  console.log(`Hey, ${person.name} is really cool!`)
}
```
**String literal type:** 
If you want to enable a couple of different strings. Very much like enums in Java.
```
/**
 * Get a string to describe the greating of me or you
 * @param { "me" | "you" }  - arg Me or you
 * @returns { String } A greeting message.
 */
function age(arg) {
  return `Hello, you are ${arg}!`;
}
```

**Capability:**
This can be used to describe what kind of capabilities an object should have, i.e. it should have a properties `age` that is of type `number`.
```javascript
/**
 * Processes an object with properties `a` and `b`.
 * @param {{a: string, b: Function}} obj - The object to process.
 * @returns {void} 
 */
function processObject(obj) {
  console.log(`Value of a: ${obj.a}`); // We know a must be a string
  obj.b(); // Invoke the function
}
```

### Define Interfaces
With the `typedef` tag, you can define your own data structures. These can then be used like types, i.e. `@returns {Person}`.

```javascript
/**
 * @typedef {Object} Person
 * @property {string} name - The name of the person.
 * @property {number} age - The age of the person.
 * @property {Function} greet - A method that returns a greeting message.
 */
```

### Generics
Using `@template`, you can use generics.

```javascript
/**
 * @template T
 * @param {T[]} array - An array of elements of type T.
 * @returns {T} The first element of the array.
 */
function getFirstElement(array) {
  return array[0];
}
```

**Functions:**
With this you can describe functions that use currying, in different degrees of precision.  
  
The most simple way to describe something as a function, that takes `A` and `B` which produces `C`.
```javascript
/**
 * A curried function that takes a string and returns another function.
 * The returned function then takes a number and returns a boolean.
 * @type { (string) => (number) => boolean }
 */
const isLongerThan = (str) => (length) => str.length > length;
```
To be a bit more precise, you can also name the parameters:
```javascript
/**
 * A curried function that takes a number `a` and returns another function.
 * The returned function takes a number `b` and returns their sum as a string.
 * @type { (a:number) => (b:number) => string }
 */
const addAndStringify = (a) => (b) => String(a + b);
```
It is also possible to throw generics into this mix:
```javascript
/**
 * A curried function that takes a value of any type `T` and returns another function.
 * The returned function takes a string and simply returns the original `T` value.
 * @type { <T> (a:T) => (message:string) => T }
 */
const echoAfterMessage = (a) => (message) => {
  console.log(message);
  return a;
};
```


## Best Practices
If you are using types, or JsDoc in general, there are a couple of best practices you may want to follow:
- **Set up your IDE properly:** it will make your life so much easier
- **Follow conventions:** pick or define a convention and stick to it
- **Add examples:** makes it so much easier to figure out how a function call should look
- **Link to documentation:** use `@link` to link to relevant documentation
- **Validate the documentation:** validate what you've documented with test cases