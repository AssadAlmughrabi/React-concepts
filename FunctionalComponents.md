# Functional Components

## Definition

A **functional component** is a JavaScript function that takes **props** and returns **JSX** (what to show on the screen).

## Why?

- It is the modern way to write React components.
- It is short and easy to read.
- It can use hooks (`useState`, `useEffect`, ...) for state and side effects.

## Example

```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
}

// using it
<Greeting name="Asaad" />
```

The same with an arrow function:

```jsx
const Greeting = ({ name }) => <h1>Hello, {name}</h1>;
```

## Notes

- The name must start with a **capital letter** (`Greeting`, not `greeting`).
- It must return **one parent element**. Use a Fragment `<>...</>` to wrap many elements.
- Before hooks, state was only possible in **class components**. Now functional components are used instead.
