# Spread Operator

## Definition

The **spread operator** (`...`) copies all items of an array or all properties of an object into a new one.

## Example

```js
// Array
const a = [1, 2];
const b = [...a, 3]; // [1, 2, 3]

// Object
const user = { name: "Asaad", age: 25 };
const updated = { ...user, age: 26 }; // { name: "Asaad", age: 26 }
```

## Notes

- It makes a **new** array/object, so the original doesn't change.
- Later properties overwrite earlier ones (`age: 26` replaces `age: 25`).
- In React, it is used to update state: `setUser({ ...user, age: 26 })`.
- The copy is **shallow**: nested objects are still shared.
