# Event Loop

## Definition

JavaScript runs **one thing at a time** (single-threaded). The **event loop** is how it still handles slow tasks (timers, fetch) without freezing: it runs them later, when the main code is finished.

## How?

1. **Call stack**: runs the normal code, line by line.
2. Slow tasks (`setTimeout`, `fetch`) are handled by the browser in the background.
3. When they finish, their callbacks wait in a **queue**.
4. The event loop moves a callback from the queue to the call stack **only when the stack is empty**.

Promise callbacks (microtasks) run **before** `setTimeout` callbacks.

## Example

```js
console.log("1");

setTimeout(() => console.log("2"), 0);

Promise.resolve().then(() => console.log("3"));

console.log("4");

// Output: 1, 4, 3, 2
```

- `1` and `4` are normal code, so they run first.
- `3` is a Promise (microtask), so it runs next.
- `2` is a `setTimeout`, so it runs last, even with `0` ms.

## Notes

- A long loop in normal code blocks everything, because the event loop waits for the stack to be empty.
