# Regular Expressions
As in pretty much every language, we can use regular expressions to either make problems go away or get more of them. Most of the times both happens.

> If you do not know about regular expressions already, start [here](https://www.geeksforgeeks.org/write-regular-expressions/).

## `test()`
Tests if a regex matches a string. Returns `true` or `false`.

```js
const regex = /cat/;
console.log(regex.test('The cat is here.')); // true
console.log(regex.test('The dog is here.')); // false
```

## `exec()`

Finds a match and returns an array with details or null if no match.

```js
const regex = /(\d+)/;
const result = regex.exec('Order 123');
console.log(result); // ["123", "123"]
console.log(result.index); // 6 (start position of match)
```

## `match()`

Finds all matches in a string. Returns an array or null.
```js
const text = 'cat, bat, rat,horse';
const regex = /\b\w{3}\b/g; // Words with exactly 3 letters
console.log(text.match(regex)); // ["cat", "bat", "rat"]
```

## `matchAll()`

Returns an iterator for all match results (with capture groups).
```js
const regex = /(\w+):(\d+)/g;
const text = 'apple:123 banana:456';

for (const match of text.matchAll(regex)) {
  console.log(match);
}
// ["apple:123", "apple", "123"]
// ["banana:456", "banana", "456"]
```

## `replace()`

Replaces matches in a string.
```js
const text = 'I have a cat.';
console.log(text.replace(/cat/, 'dog')); // "I have a dog."
```

## `search()`

Finds the first match and returns its index or -1.
```js
const text = 'The quick brown fox';
console.log(text.search(/quick/)); // 4
console.log(text.search(/slow/));  // -1 because no match
```

## `split()`

Splits a string based on a pattern.
```js
const text = 'apple, banana, cherry';
console.log(text.split(/, /)); // ["apple", "banana", "cherry"]
```