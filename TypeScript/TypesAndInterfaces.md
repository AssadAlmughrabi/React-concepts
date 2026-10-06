# Types & Interfaces

## Definition

**TypeScript** adds types to JavaScript, so mistakes are found **before** running the code.

**type** and **interface** both describe the shape of an object (which properties it has and their types).

## Example

```ts
interface User {
  name: string;
  age: number;
  email?: string; // optional
}

type Product = {
  title: string;
  price: number;
};

const user: User = { name: "Asaad", age: 25 };
const product: Product = { title: "Book", price: 10 };
```

## Notes

- **interface**: only for objects. Can be extended with `extends`.
- **type**: can be anything (objects, unions, strings): `type Status = "on" | "off";`
- In React, used for props: `function Greeting({ name }: { name: string }) {}`
