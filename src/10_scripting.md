# Scripting
A scripting language, like Java**Script**, is characterised mainly by the ability to execute arbitrary texts from sources like files, URLs, the user and so on. Other characteristics are that they are interpreted and thus have a lenient type system.
  
Normally this is a big no-no. **A very very big no-no**. But this is essentially what every browser does: load file from `example.com` and execute the code that is saved there.  
  
## Use Cases
Scripting is used at an endless amount of places:
- Command line
- Automation (DevOps)
- Build System
- Templating
- Business Rules
- Formulae
- DSL (Data Structure Language)

## Examples
Because that was a lot of theory, here a couple of examples.

### "Auto" Imports
If we want to import JavaScript files with the `<script>` tag into our HTML, we normally have to include each module in a seperate tag. This gets cumbersome fast. Instead we can dynamically create `<script>` tags, whiche then import the needed files.

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>All Tests</title>
</head>
<body>
    <script>
        ["function", "lambda"].forEach(n => 
            {
                document.writeln('<script src="' + n + '/' + n + '.js"><' + '/script>')
                document.writeln('<script src="' + n + '/' + n + 'Test.js"><' + '/script>')
            }
        );
    </script>

</body>
</html>
```
### Plotter
If we want to take a (math) function that a user gives us and evaluate it, we can do that a couple of different ways. 
The easiest way would be to call the `eval` function, which then evaluates the supplied string. 

```javascript
function start() {
  const userFunction = document.getElementById("user_function");
  const canvas = document.getElementById("canvas");

  display(canvas, (x) => eval(userFunction.value));
  userFunction.onchange = (_) =>
    display(canvas, (x) => eval(userFunction.value));
}
// lot of code missing for brevities sake
```

One problem of this approche is that it is **very very** innefficient. Instead we can use the functional programming things we learned in the weeks before and rewrite it:

```javascript
function start() {
    const userFunction = document.getElementById('user_function');
    const canvas       = document.getElementById('canvas');

    const f = _ => Function( "x", "return " + userFunction.value);
    display(canvas, f() );
    userFunction.onchange = _ => display(canvas, f() );
}
// lot of code missing for brevities sake
```

Check out [the offical WEBPR repo](https://github.com/WebEngineering-FHNW/webpr-hs24/tree/main/week5) for the entire code and even more cool examples!