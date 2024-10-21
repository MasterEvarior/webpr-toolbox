# Objects
//TODO

## Open, Dynamic

```javascript
const good = { 
    firstname : "Good", 
    lastname  : "Boy", 
    getName   : function() {  
         return this.firstname + " "  + this.lastname  
    } 
}; 
```

## Closed, Explicit

```javascript
function Person(first, last) { 
    return { 
        getName: () => first + " "  + last;                  
    } 
}
```

## Mixed, classified

```javascript
const Person = ( () => { // lexical scope     
    function Person(first, last) { // ctor, binding 
        this.firstname = first; 
        this.lastname  = last; 
    } 
    Person.prototype.getName = function() { 
           return this.firstname + " " + this.lastname; 
    }; 
    return Person; 
}) (); // IIFE 
// new Person("Good", "Boy") instanceof Person
```