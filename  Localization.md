# Localization in React

## What is it?

**Localization** means showing The app in the user's language and format (text, dates, numbers, currency).

Example: the same button shows "Buy now" in English and "اشترِ الآن" in Arabic.

## Example

Put the text for each language in one object, then pick the current language.

```jsx
const translations = {
  en: { welcome: "Welcome", buy: "Buy now" },
  ar: { welcome: "مرحبا", buy: "اشترِ الآن" },
};

function App() {
  const [lang, setLang] = useState("en");
  const t = translations[lang];

  return (
    <div dir={lang === "ar" ? "rtl" : "ltr"}>
      <h1>{t.welcome}</h1>
      <button>{t.buy}</button>
      <button onClick={() => setLang(lang === "en" ? "ar" : "en")}>
        Change language
      </button>
    </div>
  );
}
```

- Don't hard-code text inside components. Use keys like `t.welcome`.
- `dir="rtl"` makes Arabic read right-to-left.
- In real projects, use a library like **react-i18next**.

## Dates and numbers

JavaScript has the built-in `Intl` API for this:

```js
new Intl.DateTimeFormat("en-US").format(new Date()); // 10/6/2026
new Intl.NumberFormat("en-US", { style: "currency", currency: "USD" }).format(1234.5); // $1,234.50
```
