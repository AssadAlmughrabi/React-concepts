# Responsive

## Definition

**Responsive design** means the app looks good and works on **all screen sizes**: phone, tablet, and desktop.

## Why?

Users open the app on different devices. Without it, the page can be too small to read or need side scrolling on a phone.

## Example

Use CSS **media queries** to change the layout based on screen width.

```css
.cards {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columns on desktop */
  gap: 16px;
}

@media (max-width: 768px) {
  .cards {
    grid-template-columns: 1fr; /* 1 column on phone */
  }
}
```

```jsx
function CardList() {
  return (
    <div className="cards">
      <div>Card 1</div>
      <div>Card 2</div>
      <div>Card 3</div>
    </div>
  );
}
```

On desktop the cards show side by side. On a phone they stack under each other.

## Notes

- Use **Flexbox** and **Grid** for layouts that adapt.
- Use relative units (`%`, `rem`, `vw`) instead of fixed `px` widths.
- **Mobile-first**: write styles for phones first, then add `@media (min-width: ...)`
