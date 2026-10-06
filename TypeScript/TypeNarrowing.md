# Type Narrowing

## Definition

**Type narrowing** is checking a value's type so TypeScript knows the **exact type** inside that block.

## Example

```ts
function printId(id: number | string) {
  if (typeof id === "string") {
    console.log(id.toUpperCase()); // id is string here
  } else {
    console.log(id.toFixed(2)); // id is number here
  }
}
```

Before the `if`, `id` could be either type. Inside each branch, TypeScript knows which one it is.

## Notes

Common ways to narrow:

- `typeof x === "string"` for basic types.
- `Array.isArray(x)` for arrays.
- `"name" in x` to check if an object has a property.
- `x instanceof Date` for classes.
