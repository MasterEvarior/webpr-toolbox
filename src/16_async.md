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

## Coordinate Asynchronous Actions
Any asynchronous actions are prone to race-conditions and errors. So naturally, there needs to be a way to coordinate them. Here are 3 different ways to do that.

### None
If your usecase is really really simple, this may suffice. It won't hurt to try before going down a rabbit hole.

### Sequence
If your actions are asnychronously but must be executed one after another, this is the way to go. 

An easy example is this primitive scheduler:

```javascript
const Scheduler = () => {
    let inProcess = false;
    const tasks = [];
    const process = () => {

        // check if already doing something
        if(inProcess){
          return;
        }

        // check if there is something to do
        if(tasks.length < 1){
          return;
        }

        // now we are doing something
        inProcess = true;

        // execute most current task
        // and then go to the next one
        const currentTask = task.pop();
        new Promise(resolve => task(resolve))
          .then(_ => {
            inProcess = false;
            process();
          });

    };


    // add task to list
    // and start to process them in order
    const add = task => {
      tasks.unshift(task);
      process();
    };

    return {
        add: add,
        addOk: task => add(ok => { task(); ok();}) // convenience
    }
};
```

An example usage:
```javascript
const scheduler = Scheduler();
scheduler
  .add(ok => {
    setTimeout(_ => {
        console.log("A");
        ok();
    }, 100);
  });
scheduler.addOk(() => console.log("B"));
// will log A and then B
``` 

### Result Dependency
A bit more complex is the case of result dependency. This means we have `B` and `C`, which both depend on `A`. `A` must therefore be executed before `B` and `C` but just once.

A way to do this, is to wrap you values into functions, here `DataFlowVariable`. `createValue` is a function, which returns a value. If the value is undefined, execute the function and return the value. If it is already defined, just return the value. This prevents that `A` gets executed twice.

Other variables can be nested into the `createValue` function, which then get executed in turn.

```js
const DataFlowVariable = (createValue) => {
  let value = undefined;
  return () => {
    if (value !== undefined) {
      return value;
    }
    value = createValue();
    return value;
  };
};
```

```js
const x = DataFlowVariable(() => y() + 1); //this will also execute y()
const y = DataFlowVariable(() => 1); // will return 0
x() === 2
```