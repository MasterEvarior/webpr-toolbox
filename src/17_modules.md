# Modules
JavaScript modules are reusable blocks of code that encapsulate functionality, which helps to

- organize code
- make dependencies more descriptive and simple
- avoid errors through namespaces and scopes

## What are modules _not_?
- Packages, because modules don't have modules
- Dependencies, Libraries, Releases
- Units of publication
- Objects

## What are modules?
A module is code that uses `import` or `export`, simple as that.

## How to declare
Loading modules happens async and is possible in either JavaScript or HTML.

```html
<script src="./my.js" type="module">
```

In JavaScript there are a **lot** more options

```javascript
import "module-name"; // import EVERYTHING
import defaultExport from "module-name"; // import the default export
import * as name from "module-name"; // import something with a particular "alias"
import {export} from "module-name"; //import a certain thing
import {export as alias} from "module-name"; // import with alias
import {export1, export2} from "module-name"; //import multiple things
const promise = import("./my.js") // use the async function
```

Exporting logically only happens in JavaScript and there are also a **lot** of options.

```javascript
export { name1, name2, ... }; // Export multiple named items.
export function FunctionName(){...} // Export a named function.
export const name1, name2, ...; //or let // Export named constants or variables.
export class ClassName {...} // Export a named class.
export default expression; // Export a default value.
export { name1 as default, ... }; // Export `name1` as the default.
export * from ...; // Re-export everything from another module.
export { name1, name2, ... } from ...; // Re-export specific items.
```

## Impacts & rules
Using modules has a couple of impacts and rules one should be awara of:

- using modules activivates the [use strict mode](https://www.w3schools.com/js/js_strict.asp)
- export are read-only
- modules are namespaces
- modules are singleton (are always loaded only once)
- there is no global `this`
- there is no global hoisting
- modules are subject to [SOP](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)

## How to use