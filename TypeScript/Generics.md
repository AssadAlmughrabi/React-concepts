# Generics

## Definition

**Generics** let you write a function or type that works with **any type**, while still keeping the type safe. The type is passed like a parameter: `<T>`.

## Example

```ts
function first<T>(items: T[]): T {
  return items[0];
}

const n = first([1, 2, 3]);       // n is number
const s = first(["a", "b", "c"]); // s is string
```

`T` becomes `number` or `string` depending on what you pass.

## Notes

- Without generics, you would use `any`, and lose type checking.
- In React: `useState<string>("")` tells TypeScript the state is a string.
