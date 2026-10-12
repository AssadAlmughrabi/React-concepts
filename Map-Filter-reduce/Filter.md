# filter()

## Definition

**filter()** creates a **new array** with only the items that pass a condition.

## Why?

When you want to keep some items and remove others, like only even numbers or only active users.

## Example

```js
const numbers = [1, 2, 3, 4, 5];
const evens = numbers.filter((n) => n % 2 === 0);

console.log(evens); // [2, 4]
```

## Notes

- Return `true` to keep the item, `false` to remove it.
- The new array can be **shorter** than the original.
- The original array doesn't change.
- In React, `filter()` is used to delete an item from state.
