# Lambda II
This is a continuation of the "Lambda Calculus" chapter. So if you haven't read that one yet, do so [here](./5_lambda.md).

## Atomic Lambdas
With the things we learned, we can defined *atomic* lambda terms, which are the most basic terms. You should have seen these already:
```js
const id = x => x;
const konst => x => y => x;
```
  
These two allow us to derive pretty much everything needed from them. Basic things such as `true`, `false`, `or` and so on. See a couple of those here:
```js
const T = konst;
const F = snd;

const and = a => b => a (b) (a);
const or = a => b => a (a) (b);
//.. and more
```

## Pair, Product Type
The preparation of those "basic" things, allow us to do more complex things. For example define a pair (or product) type.

```js
const Pair = x => y => f(x)(y);
const fst = p => p(T);
const snd = p => p(F);
```
This basically defined a function which "holds" two values. The `fst` and `snd` functions allow us to retrieve the first and second value respectively.  

If we expand this concept a bit it allows us to do crazy things. See the code below. It is very Haskell like but just in JavaScript.
```js
//This defines a person "object" that is a pair of a names and an age. The names are also a pair themselves.
const person = 
    firstname =>
    lastname =>
    age => 
    pair(pair(firstname)(lastname)(age));

//These functions can read the values
const firstn = p => fst(fst(p));
const lastn = p => snd(fst(p));
const firstn = p => snd(p);
```

## Immutability and Lazy
Using this style of programming has two advantages:
    - the "objects" are immutable, means you cant change them
    - they are lazily evaluated, means they compute on demand not before

## Either Function
Armed with that knowledge, we can create an `either` function. This function should execute either one lambda or another, depending on the result of a first function.

```js
const Left = x => f => g => f(x); //take the argument and execute function g
const Right = x => f => g => g(x); //take the argument and execute function g
const either = e => f => g => e(f)(g); //if e evaluates to true, execute f else execute g



//we then invoke it like that
const someFunc = true ? Left("This would be called if it were evaluated as false") : Right("This is actually called");
either (someFunc)(x => console.log(x => "Never called anyway"))(x => "This returns: " + x);


```