# Logging
JavaScript logging is similar to logging in basically every other language.

## Basic Log Levels
JavaScript offers several built-in logging methods, each with a specific purpose. The most commonly used are:

```js
console.log('Just general output');
```
Used for general output of information to the console. It's often used for basic debugging or status messages.

```js
console.info('Some basic information');
```
Used to display informational messages that are not errors but important to note.

```js
console.warn('Hey this could be important');
```
Used to indicate potential problems or warnings that don't stop the execution of the program but might lead to issues.

```js
console.error('SOMETHING HAS GONE WRONG');
```
Used to log error messages when something goes wrong, especially when an exception occurs.

```js
console.debug('Psst, I am a sneaky message');
```
Used for detailed debugging information. In some browsers, these messages may be hidden by default unless you enable verbose logging.

## Logging Objects
It is also possible to pass entire objects or arrays of objects to the logging functions. These then get logged out nicely, in JSON.
```js
const user = {
  name: 'Alice',
  age: 30,
  occupation: 'Engineer'
};

console.log('User object:', user);
```
This will result in something like this (may look different depending on your browser):
```js
User object: Object { name: "Alice", age: 30, occupation: "Engineer" }
```

Of course the same also works for arrays of objects.
```js
const users = [
  { name: 'Alice', age: 30 },
  { name: 'Bob', age: 25 },
  { name: 'Charlie', age: 35 }
];

console.log('Array of users:', users);
```
Which then results in:
```js
Array of users: Array(3) [ ​0: Object { name: "Alice", age: 30 }, 1: Object { name: "Bob", age: 25 }, 2: Object { name: "Charlie", age: 35 } ]
```

*Fun fact: you can also display an array as a table with the `console.table()` function!*

