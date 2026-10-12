# reduce()

## Definition

**reduce()** combines all items of an array into **one value**.

## Why?

When you want one result from a whole list, like a sum or a cart total.

## Example

```js
const numbers = [1, 2, 3, 4];
const sum = numbers.reduce((acc, n) => acc + n, 0);

console.log(sum); // 10
```

- **acc** (accumulator): the result so far. It starts at `0` (the second argument).
- **n**: the current item.
- Whatever you return becomes the new `acc` for the next item.

`acc` starts at `0`, then adds each number: 0+1=1, 1+2=3, 3+3=6, 6+4=10.

## Notes

- **map**: changes every item and returns an array of the same length.
- **filter**: keeps some items and returns an array that can be shorter.
- **reduce**: combines all items and returns one value.
