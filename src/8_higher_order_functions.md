# Higher Order Functions
Higher order functions are functions which receive other functions as arguments. Most commonly they are used on collection data structures, such as lists and arrays. For the sake of simplicity we will use arrays here.

## Map
A very basic higher order function is `map()` where a function is applied to each value inside of an array. The function then returns a new array.

```js
[1,2,3].map(x => x *2);
// this results in a new array with the values [2,4,6]
```

Instead of writing the lambda each and every time, we can also define it beforehand. If we use currying we can even decide how much we want to abstract.
```js
const multiply = a => b => a * b;
const multiplyBy2 = multiply(2)

[1,2,3].map(x => x *2);
[1,2,3].map(x => multiplyBy2(x));
[1,2,3].map(multiplyBy2);
```
Which way is the best is mostly personal preference.

## Filter
The `filter()` function creates a new array with all elements that pass the test defined by the provided function. It only returns the elements that evaluate to true.

```js
const odd = x => x %2 == 1;

[1,2,3].filter(x => odd(x));// new array with the value(s) [2]
[1,2,3].filter(odd);// same thing as above but written differently
``` 

## Reduce
The `reduce()` function executes a provided reducer function on each element of the array, resulting in a single output value. It's used for aggregating data like summing up an array.

```js
const sum = (accu, cur) => accu + cur;

[1,2,3].reduce(sum);// output: 6 (which is 1 + 2 + 3)
``` 

## Apply Multiple Functions
These functions can of course be chained together.

```js
const numbers = [1, 2, 3, 4, 5];

const result = numbers
  .filter(num => num % 2 === 0)   // results in [2, 4]
  .map(num => num * 2)            // results in [4, 8]
  .reduce((acc, curr) => acc + curr, 0); // then finally returns 12
```