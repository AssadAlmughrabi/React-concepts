# useRef

## Definition

**useRef** is a React hook that keeps a value between renders **without causing a re-render** when it changes. It is also used to access a DOM element directly.

## Why?

- To focus an input, scroll to an element, or read its size.
- To store a value (like a timer id) that shouldn't update the screen.

## Example

```jsx
import { useRef } from "react";

function SearchBox() {
  const inputRef = useRef(null);

  return (
    <>
      <input ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus</button>
    </>
  );
}
```

- `useRef(null)` creates an object: `{ current: null }`.
- `ref={inputRef}` makes React put the input element in `inputRef.current`.

## Notes

- Changing `ref.current` does **not** re-render the component.
- **useState**: the value is shown on screen. **useRef**: the value is not shown on screen.
