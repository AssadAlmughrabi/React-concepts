# useContext

## Definition

**useContext** is a React hook that reads a value from a **context**, so a component can get data without receiving it as props.

## Example

```jsx
import { createContext, useContext } from "react";

const ThemeContext = createContext("light");

function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Button />
    </ThemeContext.Provider>
  );
}

function Button() {
  const theme = useContext(ThemeContext);
  return <button>Theme: {theme}</button>; // Theme: dark
}
```

## Notes

- The component re-renders when the context value changes.
- For the full explanation, see `ContextApi.md`.
