# Promise
Promises are used for asynchronous operations in JavaScript, thus representing a value that may be available *now*, *later* or *never*.

One of the most prominent uses is `fetch`, i.e: 
```js
fetch ('http://fhnw.ch/json/students/list')
    .then(response => response.json())
    .then(students => console.log(students.length))
    .catch (err => console.log(err)
```

## Structure
Each promise is a function, which receives two other functions as arguments:  
- one if everything works out
- one if something goes wrong

That may look something like this:
```js
const processEven = i => new Promise( (resolve, reject) => {
    if (i % 2 === 0) {
        resolve(i);
    } else {
        reject(i);
    }
);
```

## `.then`, `.catch` and `finally`
The `.then` function can be used to chain mutliple functions together or handle the result, which is very handy.

`.catch` on the other hand, to do something if and error gets thrown. Pretty much like in Java.

`.finally` is also lifted from Java, where it executed at the end in all cases.
```js
processEven(4)
    .then ( it => {console.log(it); return it} )
    .then ( it => processEven(it+1))
    .catch( err => console.log( "Error: " + err))
    .finally(console.log("This will always be logged"))
``` 

## Auto Promotion
Some may have noticed that in the example above, we never return a promise and still we can call the `.then` method. What kind of sorcery is this?

The sorcery is called _auto promotion_ and is a quite handy feature. It  refers to the fact that any non-Promise value passed to a resolve function (or returned by a then handler) is automatically wrapped in a resolved Promise. 