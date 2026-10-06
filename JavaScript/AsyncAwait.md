# async/await

## Definition

**async/await** is an easier way to work with Promises. It makes async code look like normal step-by-step code.

- `async` before a function makes it return a Promise.
- `await` waits for a Promise to finish before going to the next line.

## Example

```js
async function getUsers() {
  try {
    const res = await fetch("https://api.example.com/users");
    const data = await res.json();
    console.log(data);
  } catch (error) {
    console.log("Error:", error);
  }
}
```

## Notes

- `await` only works inside an `async` function.
- Use `try/catch` to handle errors (instead of `.catch()`).
- It is the same as `.then()` chains, just easier to read.
