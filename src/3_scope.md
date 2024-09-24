# Scope  
Strictly speaking JavaScript only has two scopes:
- `global` the entire window (if you are in a Browser)
- `function` variables are alwayes local to the enclosing functions

Despite just having two scopes, JavaScript gives us four different ways to declare variables.

**Number 1:**
```js
x = 12;
```
This creates a mutable global variable. This is not good for obvious reasons. **DONT DO THIS!**

**Number 2:**
```js
var x = 12;
```
This creates a mutable hoisted variable. What does "hoisted mean? It means that the variable gets initialized at the beginning of the scope, even if we declare it further down. Which causes things like this:
```js
x = 0;
function foo(){
    document.writeln(x); //this prints undefined, not 0
    var x = 12;
}
```
This is also not good for also obvious reasons. **DONT DO THIS!**

**Number 3:**
```js
let x = 12;
```
This creates a mutable variable inside of the local scope. This is good, use this.


**Number 4:**
```js
const x = 12;
```
This creates an immutable variable inside of the local scope. Immutable meaning *not reasignable*, not really immutable. This is good, use this.
