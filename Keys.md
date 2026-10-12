# Keys

## Definition

A **key** is a special prop you give to each item when rendering a list. It helps React know which item is which.

## Why?

When a list changes (add, delete, reorder), React uses keys to update only the items that changed instead of re-creating the whole list.

## Example

```jsx
const users = [
  { id: 1, name: "Asaad" },
  { id: 2, name: "Sara" },
];

function UserList() {
  return (
    <ul>
      {users.map((user) => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

## Notes

- Keys must be **unique** among siblings in the same list.
- Use a stable id from your data (like `user.id`).
- Avoid using the **index** as a key if the list can change order or have items deleted. It can show the wrong data.
