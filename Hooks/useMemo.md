# useMemo

## Definition

**useMemo** is a React hook that remembers (caches) the result of a calculation between re-renders, and only recalculates it when its dependencies change.

## Why?

Every time a component re-renders, all the code inside it runs again. `useMemo` helps in two cases:

1. **Slow calculations**: skip running them again if the inputs didn't change.
2. **Keeping the same reference**: an object or array created inside a component is new on every render. `useMemo` keeps the same one, so things that compare by reference (Context `value`, `React.memo` props, `useEffect` dependencies) don't see a "change".

## How?

```jsx
const result = useMemo(() => {
  return calculateSomething(a, b);
}, [a, b]);
```

- The first argument is a function that returns the value.
- The second argument is the **dependency array**.
- React recalculates only when a value in the dependency array changes. Otherwise it returns the cached result.

## Example 1: slow calculation

```jsx
import { useMemo, useState } from "react";

function ProductList({ products }) {
  const [search, setSearch] = useState("");
  const [dark, setDark] = useState(false);

  const filtered = useMemo(() => {
    console.log("filtering...");
    return products.filter((p) => p.name.includes(search));
  }, [products, search]);

  return (
    <div className={dark ? "dark" : ""}>
      <input value={search} onChange={(e) => setSearch(e.target.value)} />
      <button onClick={() => setDark(!dark)}>Toggle theme</button>
      <ul>
        {filtered.map((p) => (
          <li key={p.id}>{p.name}</li>
        ))}
      </ul>
    </div>
  );
}
```

Typing in the search box filters again. Clicking "Toggle theme" re-renders the component, but it **doesn't** filter again because `products` and `search` didn't change.

## Example 2: same reference for Context

```jsx
const value = useMemo(() => ({ user, setUser }), [user]);

<UserContext.Provider value={value}>
```

Without `useMemo`, `{ user, setUser }` is a new object on every render, and every component that uses the context re-renders.

## When NOT to use it

- For simple, fast calculations like `a + b`. `useMemo` has its own cost, so it can make things slower.
- Use it only when a calculation is slow or when you need to keep the same reference.

## useMemo vs useCallback vs React.memo

- **useMemo** remembers a **value** (the result of a function).
- **useCallback** remembers a **function** itself.
- **React.memo** remembers a **component's render**: it skips re-rendering the component if its props didn't change (compared by reference).
