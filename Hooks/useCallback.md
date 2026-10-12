# useCallback

## Definition

**useCallback** remembers a **function** between re-renders, so it stays the same function until its dependencies change.

## Why?

Every re-render creates every function again as a new one. If you pass it to a child wrapped in `React.memo`, the child sees a changed prop and re-renders anyway.

## Example

```jsx
import { memo, useCallback, useState } from "react";

const Button = memo(function Button({ onClick }) {
  return <button onClick={onClick}>Add</button>;
});

function Counter() {
  const [count, setCount] = useState(0);
  const [dark, setDark] = useState(false);

  const increment = useCallback(() => {
    setCount((c) => c + 1);
  }, []);

  return (
    <div className={dark ? "dark" : ""}>
      <p>{count}</p>
      <Button onClick={increment} />
      <button onClick={() => setDark(!dark)}>Toggle theme</button>
    </div>
  );
}
```

Clicking "Toggle theme" re-renders `Counter`, but not `Button`, because `increment` is the same function.

## Notes

- `useCallback` alone doesn't stop re-renders. It helps only with `React.memo` or dependency arrays (`useEffect`).
- **useCallback** remembers a function. **useMemo** remembers a value.
