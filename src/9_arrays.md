# Arrays
A small excurse into more JavaScript arrays functions. 

## push()
Adds one or more elements to the end of an array and returns the new length of the array.
  
```javascript
let fruits = ["apple", "banana"];
fruits.push("orange"); // returns 3
console.log(fruits);  // output: ["apple", "banana", "orange"]
```

## pop()
Removes the last element from an array and returns that element.
  
```javascript
let fruits = ["apple", "banana", "orange"];
let lastFruit = fruits.pop();
console.log(lastFruit);  // output: "orange"
console.log(fruits);     // output: ["apple", "banana"]
```

## shift()
Removes the first element from an array and returns that element.
  
```javascript
let fruits = ["apple", "banana", "orange"];
let firstFruit = fruits.shift();
console.log(firstFruit);  // output: "apple"
console.log(fruits);      // output: ["banana", "orange"]
```

## unshift()
Adds one or more elements to the beginning of an array and returns the new length of the array.
  
```javascript
let fruits = ["banana", "orange"];
fruits.unshift("apple");
console.log(fruits);  // output: ["apple", "banana", "orange"]
```

## slice()
Is used to slice (hence the name) a part out of the array.

```javascript
let fruits = ["banana", "orange", "grape"];
const sliced = fruits.slice(1,3); // 1 is inclusive, 3 not
console.log(sliced);  // output: [ "orange", "grape" ]

const sliced2 = fruits.slice(1); // until the end of the array
console.log(sliced2);  // output: [ "orange", "grape" ]

const sliced3 = fruits.slice(0, -1); // until -1 the length of the array
console.log(sliced3);  // output: [ "banana", "orange" ]
```

## splice()
Changes the contents of an array by removing, replacing, or adding elements at specific positions.
```javascript
// removing elements
let fruits = ["apple", "banana", "orange", "grape"];
fruits.splice(1, 2);  // Removes 2 elements starting from index 1
console.log(fruits);  // Output: ["apple", "grape"]

// adding elements
let fruits = ["apple", "banana", "grape"];
fruits.splice(2, 0, "orange", "kiwi");  // Adds "orange" and "kiwi" at index 2
console.log(fruits);  // Output: ["apple", "banana", "orange", "kiwi", "grape"]

//replacing elements
let fruits = ["apple", "banana", "orange"];
fruits.splice(1, 1, "kiwi");  // Replaces 1 element at index 1 with "kiwi"
console.log(fruits);  // Output: ["apple", "kiwi", "orange"]

```

## Create arrays
With the `from` method, you can create an array from every object that has a `length` property
```javascript
Array.from("abc") //output ["a", "b", "c" ]
Array.from({length: 2}) //output [undfined, undefined]
```
This can also be used to create very large arrays in an easy way.
```javascript
Array.from({length: 1000}, (it, idx) => idx) //output [0, 1, ..., 999 ]
```
