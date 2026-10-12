# Closures

## Definition

A **closure** is when a function **remembers the variables from where it was created**, even after the outer function has finished.

## Example

```js
function createCounter() {
  let count = 0;

  return function () {
    count++;
    return count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

`createCounter` finished, but the inner function still remembers `count`.

## Notes

- Used to keep data private (no one outside can change `count` directly).
- In React, every function inside a component is a closure: it sees the props and state **from the render it was created in**.
