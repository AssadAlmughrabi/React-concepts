# useState

## Definition

**useState** is a React hook that lets a component **remember a value** (state). When the state changes, the component re-renders to show the new value.

## Why?

A normal variable resets on every render, and changing it doesn't update the screen. State keeps the value and updates the UI.

## Example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>Clicked {count}</button>;
}
```

- `count`: the current value. It starts at `0`.
- `setCount`: the function to change it.
- Calling `setCount` re-renders the component with the new value.

## Notes

- Don't change state directly (`count = 5`). Always use the setter (`setCount(5)`).
- If the new value depends on the old one, use a function: `setCount((c) => c + 1)`.
- For objects and arrays, create a new copy instead of changing the old one: `setUser({ ...user, name: "Asaad" })`.
