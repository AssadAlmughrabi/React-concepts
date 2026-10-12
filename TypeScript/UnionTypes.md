# Union Types

## Definition

A **union type** means a value can be **one of several types**. It uses `|` (or).

## Example

```ts
let id: number | string;
id = 10;      // OK
id = "abc";   // OK
id = true;    // Error

type Status = "loading" | "success" | "error";
let status: Status = "loading";
```

## Notes

- Union of exact values (like `Status`) limits a variable to only those values.
- Before using a union value, you often need to check which type it is (see `TypeNarrowing.md`).
