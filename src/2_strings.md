# Strings
A small excursion into strings and how to declare them in JavaScript.  

You can declare them the same way as you would declare in Java.
```js
"This is a string"
```
You can also declare them like you would a single character in Java.
```js
'This is also a String'
```

More interesting is the declaration with backticks(`` ` ``). With this you can declare a multiline strings and even use string interpolation!
This allows us to build nice little templates, which is why we also call these strings "template strings".
```js
`
This
is
a
multiline
string :)
`

let x = 1;
`
This is {x} template
`
```

A more obscure way to declare strings is to use forward slashes(`/`), like so:
```js
/test/
//put this into a constructor
String(/eins/)
```
Huh? Why does this work? What does this do?
    
The answer is simple, forward slashes denote a [regular expression](https://en.wikipedia.org/wiki/Regular_expression) in JavaScript. Because a regular expression is usually just a string that gets parsed, putting this into a string constructor also yields a string.