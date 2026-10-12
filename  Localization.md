# Localization

## Definition

**Localization** means showing the app in the user's language and format (text, dates, numbers, currency).

## Why?

So users from different countries can use the app in their own language.

## Example

```jsx
const translations = {
  en: { buy: "Buy now" },
  ar: { buy: "اشترِ الآن" },
};

function App() {
  const [lang, setLang] = useState("en");

  return (
    <div dir={lang === "ar" ? "rtl" : "ltr"}>
      <button>{translations[lang].buy}</button>
      <button onClick={() => setLang(lang === "en" ? "ar" : "en")}>
        Change language
      </button>
    </div>
  );
}
```

Clicking "Change language" switches the text between English and Arabic.

## Notes

- Don't hard-code text in components. Keep it in one place per language.
- `dir="rtl"` makes Arabic read right-to-left.
- In real projects, use a library like **react-i18next**.
- For dates and numbers, use the built-in `Intl` API.
