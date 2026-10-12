# Context API

## Definition

**Context API** is a way to share data across the component tree without passing props manually through every level.

## Why?

Without context, if `App` has data and a deep child needs it, you must pass it through every component in between, even ones that don't use it. This is called **prop drilling**.

```text
App (user) -> Layout (user) -> Navbar (user) -> Avatar (uses user)
```

With context, `Avatar` reads `user` directly.

## How? (3 steps)

1. **Create** a context with `createContext()`.
2. **Provide** a value higher up in the tree with `<MyContext.Provider value={...}>`.
3. **Read** the value in any component below with `useContext(MyContext)`.

## Example

```jsx
import { createContext, useContext } from "react";

// 1. Create
const UserContext = createContext();

function App() {
  // 2. Provide
  return (
    <UserContext.Provider value="Asaad">
      <Navbar />
    </UserContext.Provider>
  );
}

function Navbar() {
  return <Avatar />; // no props passed
}

function Avatar() {
  // 3. Read
  const user = useContext(UserContext);
  return <p>Hello, {user}</p>;
}
```

## Context and re-rendering

When the `value` changes, **every** component that uses `useContext(UserContext)` re-renders, even if it only uses a part of the value that didn't change. This can cause extra re-renders and slow the app, so we need to structure and memoize context carefully.

React checks if the value changed by comparing the **reference** (`Object.is`), not the content.

### Problem: new object every render

```jsx
function App() {
  const [user, setUser] = useState("Asaad");
  // new object on every render of App, so all consumers re-render every time
  return (
    <UserContext.Provider value={{ user, setUser }}>
      <Navbar />
    </UserContext.Provider>
  );
}
```

### Fix 1: memoize the value with `useMemo`

```jsx
const value = useMemo(() => ({ user, setUser }), [user]);

<UserContext.Provider value={value}>
```

Now the object only changes when `user` changes.

### Fix 2: split into smaller contexts

Don't put everything in one big context. Use separate ones (`ThemeContext`, `UserContext`), so changing the theme doesn't re-render components that only use the user.

**Note:** `React.memo` does **not** stop a component from re-rendering when the context it uses changes.

**Common uses:** theme (dark/light), logged-in user, language.
