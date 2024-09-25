# Lambda Calculus
Lambda calculus describes can describe all the operations one can do on a computer. This can help us to understand (JavaScript) code.

## Basics
Lambda calculus has three operations:
- α => Rename parameter 
- β => Apply argument 
- η => Cancel parameter

Technically we only need α and β, from those two we could then infer η. Too keep it simple, we will not do that and, instead, look at η as a single operation.

## Alpha Translation (α)
This operation allows us to rename things. This is really simple, like so:
```js
const id = x => x
```

## Beta Reduction (β)
All this operation does is `search x on the left and replace it with x on the right`.

Practically this may look like this:
```
(x => x)(1) //x is our foo(x) and (1) is the method call foo(1)
(1 => x)(1) //if we replace our x with the input it looks like this
(1 => 1)(1) //which means that the output x is also 1...
1 // and which means everything cancels each other out
```

## Eta Reduction (η)
If we have an expression where on the right-most left is a parameter and on the right-most right is exactly an input, which is equivalent to the parameter, we can remove both of those.

Sounds complicated, is really simple:
```
x => foo (x) //right-most parameter and input is both x
foo // so this is foo
```

If we have more than one parameter or input, we always have to remember to focus on the right-most:
```
x => y => both(x)(y)
x => both(x) //remove the y
both //remove the x
```