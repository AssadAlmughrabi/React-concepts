# useEffect

## Definition

**useEffect** is a React hook that runs code **after** the component renders. It is used for side effects: things outside of rendering, like fetching data, timers, or changing the page title.

## How?

```jsx
useEffect(() => {
  // code to run
}, [dependencies]);
```

The dependency array decides **when** it runs:

- `[]` : only once, after the first render.
- `[count]` : after the first render and every time `count` changes.
- no array : after **every** render.

## Example

```jsx
import { useEffect, useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Clicked ${count} times`;
  }, [count]);

  return <button onClick={() => setCount(count + 1)}>Click</button>;
}
```

Every time `count` changes, the page title updates.

## Notes

- **Cleanup**: return a function from the effect to clean up (stop a timer, remove a listener). React runs it before the next effect and when the component is removed.

  ```jsx
  useEffect(() => {
    const id = setInterval(() => console.log("tick"), 1000);
    return () => clearInterval(id);
  }, []);
  ```

- Don't forget dependencies: every value from the component used inside the effect should be in the array.
