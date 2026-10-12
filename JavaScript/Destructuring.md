# Destructuring

## Definition

**Destructuring** is a short way to take values out of an **array** or **object** and put them into variables.

## Example

```js
// Object
const user = { name: "Asaad", age: 25 };
const { name, age } = user;
console.log(name); // "Asaad"

// Array
const colors = ["red", "green"];
const [first, second] = colors;
console.log(first); // "red"
```

## Notes

- Objects use `{}` and match by **name**. Arrays use `[]` and match by **position**.
- Default value: `const { city = "Unknown" } = user;`
- In React, you use it all the time: `const [count, setCount] = useState(0);` and `function Greeting({ name }) {}`.
