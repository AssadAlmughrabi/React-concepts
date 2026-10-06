# Re-render

## Definition

A **re-render** is when React runs a component function again to check if the UI needs to change.

Re-render doesn't always mean the page changes. React compares the new result with the old one and only updates the DOM where something is different.

## When does a component re-render?

1. Its **state** changes (`useState`).
2. Its **parent** re-renders (even if the props are the same).
3. A **context** it uses changes (`useContext`).

## Example

```jsx
function App() {
  const [count, setCount] = useState(0);

  return (
    <>
      <button onClick={() => setCount(count + 1)}>Clicked {count}</button>
      <Child />
    </>
  );
}

function Child() {
  console.log("Child rendered");
  return <p>I am a child</p>;
}
```

Clicking the button changes `count`, so `App` re-renders, and `Child` re-renders too because its parent did.

## How to avoid extra re-renders

- **React.memo**: skip re-rendering a child if its props didn't change.
- **useMemo**: keep the same object/array between renders.
- **useCallback**: keep the same function between renders.
- **Split context**: use small contexts so a change doesn't re-render everything.

## Notes

- Re-renders are normal and usually fast. Only optimize when something is slow.
