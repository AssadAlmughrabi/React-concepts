# map()

## Definition

**map()** creates a **new array** by changing every item of the original array.

## Why?

When you want to change every item in a list, like doubling numbers or turning data into JSX.

## Example

```js
const numbers = [1, 2, 3];
const doubled = numbers.map((n) => n * 2);

console.log(doubled); // [2, 4, 6]
```

## Notes

- The new array has the **same length** as the original.
- The original array doesn't change.
- In React, `map()` is used to render lists. Each item needs a `key`.
