# Async & Await
`async` and `await` are syntactic sugar for Promises. So if you haven't read that section yet, go read it.

 They make asynchronous code look and behave more like synchronous code, improving readability and reducing the need for chaining `.then()` and `.catch()`.

## `async`
A function can be declared as `async` by using the `async` keyword (obviously). Every function that is declared as such, will return a resolved promise.

```js
async function add(a, b) {
  return a + b; // Automatically wrapped in a Promise
}

add(2, 3)
    .then((result) => console.log(result)); // Logs: 5
```

## `await`
`await` is used inside of `async` functions, on other functions that return Promises. It pauses the execution until the promise is resolved and then returns the resolved value. 

```js
async function fetchData() {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  console.log(data);
}

fetchData(); // Logs the fetched data
```