# Common Components

## Definition

**Common components** are the built-in browser elements you use in JSX, like `<div>`, `<p>`, `<button>`, `<input>`, and `<img>`. They all share the same common **props** and **events**.

## Common props

- `className`: CSS class (not `class`, because `class` is a JavaScript word).
- `style`: inline styles as an object, with camelCase names: `style={{ fontSize: 20 }}`.
- `children`: the content between the opening and closing tags.
- `ref`: gives access to the real DOM element (see `useRef.md`).
- `key`: used when rendering lists (see `Keys.md`).

## Common events

- `onClick`: when the element is clicked.
- `onChange`: when an input value changes.
- `onSubmit`: when a form is submitted.

Event names are **camelCase** (`onClick`, not `onclick`) and take a function, not a string.

## Example

```jsx
function Form() {
  const handleSubmit = (e) => {
    e.preventDefault(); // stop the page from reloading
    console.log("submitted");
  };

  return (
    <form onSubmit={handleSubmit}>
      <input className="input" onChange={(e) => console.log(e.target.value)} />
      <button style={{ color: "blue" }}>Send</button>
    </form>
  );
}
```

## Notes

- Use `htmlFor` instead of `for` on `<label>`.
- Lowercase tags (`<div>`) are browser elements. Capitalized tags (`<Form>`) are your own components.
