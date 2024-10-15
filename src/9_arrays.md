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