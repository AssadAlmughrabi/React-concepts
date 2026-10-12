# React.memo

## Definition

**React.memo** wraps a component and skips re-rendering it if its **props didn't change**.

## Why?

When a parent re-renders, all its children re-render too, even if their props are the same. `React.memo` stops that.

## Example

```jsx
import { memo, useState } from "react";

const Greeting = memo(function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
});

function App() {
  const [count, setCount] = useState(0);

  return (
    <>
      <Greeting name="Asaad" />
      <button onClick={() => setCount(count + 1)}>Clicked {count}</button>
    </>
  );
}
```

Clicking the button re-renders `App`, but not `Greeting`, because `name` didn't change.

## Notes

- Objects and functions are new on every render, so `memo` sees them as changed. Use `useMemo` for objects and `useCallback` for functions.
- `memo` doesn't stop re-renders from the component's own state or from context.
