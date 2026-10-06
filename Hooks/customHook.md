# Custom Hook

## Definition

A **custom hook** is the function that uses React hooks so you can reuse the same logic in many components.

Its name must start with **`use`** (like `useToggle`, `useFetch`,`useTodo`).

## Why?

When two components have the same logic, you move it into a custom hook instead of copying it.

## Example

```jsx
import { useState } from "react";

// custom hook
function useToggle() {
  const [on, setOn] = useState(false);
  const toggle = () => setOn(!on);
  return [on, toggle];
}

// using it
function Menu() {
  const [open, toggleOpen] = useToggle();

  return (
    <>
      <button onClick={toggleOpen}>Menu</button>
      {open && <p>Menu is open</p>}
    </>
  );
}
```

`useToggle` holds the on/off logic. Any component can use it instead of writing `useState` and `toggle` again.

## Notes

- Each component that uses the hook gets **its own state**. They don't share it.
- Custom hooks follow the same rules as other hooks: call them only at the top level of a component, not inside `if` or loops.
