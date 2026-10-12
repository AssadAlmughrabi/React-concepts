# Props vs State

## Definition

- **Props**: data a component **receives from its parent**. The component can't change them (read-only).
- **State**: data a component **owns and manages itself**. It can change it with `useState`.

## Example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0); // state

  return (
    <>
      <Display value={count} /> {/* passing state as a prop */}
      <button onClick={() => setCount(count + 1)}>Add</button>
    </>
  );
}

function Display({ value }) {
  return <p>Count: {value}</p>; // prop (read-only)
}
```

- `count` is **state** in `Counter`, because `Counter` owns and changes it.
- `value` is a **prop** in `Display`, because it comes from the parent.

## Notes

- **Props** come from the parent; **state** lives inside the component.
- **Props** are read-only; **state** can change with its setter.
- A change in either one re-renders the component.
- A child can't change its props. To change the parent's state, the parent passes a function as a prop (like `onAdd={() => setCount(count + 1)}`).
