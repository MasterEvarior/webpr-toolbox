# Objects
The idea of objects is to be data structures with their associated methods and state. The same as in (almost) every other programming language.

## Ways to create Objects
There are many different ways to create objects in JavaScript. Each with their advantages and disadvantages.

### Open, Dynamic
Very simpel way to create objects. This way is very dynamic and easy to manipulate. This is also its main disadvantage, along with the inability to enforce and share its structure.

Using `this` also has major problems, which you can read more about [here](https://www.freecodecamp.org/news/removing-javascripts-this-keyword-makes-it-a-better-language-here-s-why-db28060cc086/).

```javascript
const good = { 
    firstname : "Good", 
    lastname  : "Boy", 
    getName   : function() {  
         return this.firstname + " "  + this.lastname  
    };
}; 
```

### Closed, Explicit
This solves our problems from before. It is basically a constructor, which means that the structure is always the same. It is also not possible to change the first or lastname property afterwards. This may be good or bad, depending on what you want to do with it.

```javascript
function Person(first, last) { 
    return { 
        getName: () => first + " "  + last;                  
    } 
}
```

### Mixed, classified
Here, both of the examples from before are mixed together.  
  
This is essentially a very elaborate constructor from our first version. Each function has a property `prototype`, which defines the name of it. With the "newish" `new` keyword, a new empty object is silently passed to this function. Which then means we can use `this` more like we are accustomed to from Java.

This is the "default" (if there is such a thing in JavaScript) way to create new objects.

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

## Prototyp
The prototype is a sort of "type" of object. It is itself also an objects. Using prototypes, it is possible to use things like `instanceof`.