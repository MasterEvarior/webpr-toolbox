# Classes
JavaScript has two keyword, which are relevant for this chapter: `class` and `extends`.

## `class` Keyword
The `class` keyword is syntactic sugar for the [mixed way to create objects](http://127.0.0.1:3000/book/11_objects.html#mixed-classified). There are a couple of minor difference, which will no be covered here, but it looks very similar.

A new class can be created like this:
```javascript
class Person { 
    constructor(first, last) {
        this.firstname = first;
        this.lastname = last;
    }
    getName() {
        return this.firstname + " " + this.lastname;
    }
}
// new Person("Good", "Boy") instanceof Person
```

## `extends` Keyword
JavaScript does **NOT** have real inheritance[^real].

You can use the `extends` keyword like you would in Java. But there will be no warning if you forget a call to `super`.
```javascript
class constructor Student extends Person { 
    constructor (first, last, grade) {
        super(first, last); // Do not forget!
        this.grade = grade;
    }
    getGrade(){
        return this.grade;
    }
}
const s = new Student("Top","Student", 5.5);
```
But what does actually happen if this is not real inheritance? Instead prototype chaining is used.

## What is Prototype Chaining
Each JavaScript object has a `__proto__` object, which can link it to another object. In our example above, the `Student` has a `__proto__` object which links to the `Person` prototype.

If you then call a method on a student object, it will first search if `Student` itself has a method with that name. If not it will look at the prototype, inside of the `__proto__` property. This will then go up the chain (see where the name comes from?) until the `__proto__` property is `null`. Then we know that no such method exists.

```javascript
const s = new Student("Top","Student", 5.5);
s.getName(); // calls the method in Person
s.getGrade(); // calls the method in Student
```

## Problems with Prototyp Chaining
Because everybody has access to the prototype via `__proto__` everybody can change at any time this prototype. This will propagated to all other instances.  

It is also possible to replace the prototype at runtime.
```javascript
Object.setPrototypeOf(obj, proto);
```
## Using Delegation Instead
Instead of using `class` and `extends`, we can also use delegation.

```javascript
 function Person(worker) {
    const worklog = [];
    return {
      worklog: worklog,
      work: () => worklog.push(worker.work()),
    };
  }
  const manager = Person({ work: () => "" });

  function Student(name) {
    return {
      name: name,
      work: () => name + " filled quiz",
    };
  }
  const p = Person(Student("top"));
```


[^real]: Depending on what you consider real inheritance of course.