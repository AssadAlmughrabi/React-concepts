# Promises

## Definition

A **Promise** is an object that represents a value that will be ready **later** (like data from a server). It can be:

- **pending**: still waiting.
- **fulfilled**: finished successfully, with a value.
- **rejected**: failed, with an error.

## Why?

Some tasks take time (fetching data, timers). A Promise lets the code continue and handle the result when it is ready.

## Example

```js
fetch("https://api.example.com/users")
  .then((res) => res.json())
  .then((data) => console.log(data))
  .catch((error) => console.log("Error:", error));
```

- `.then()` runs when the Promise is fulfilled.
- `.catch()` runs when the Promise is rejected.

## Notes

- Created with `new Promise((resolve, reject) => { ... })`.
- `async/await` is an easier way to write Promises (see `AsyncAwait.md`).
