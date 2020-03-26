# Intl.NumberFormat

Today I learned how to fomat number as currency using the [ECMAScript Internationalization API](https://hacks.mozilla.org/2014/12/introducing-the-javascript-internationalization-api/).

> The **Intl.NumberFormat** object is a constructor for objects that enable language sensitive number formatting.

## USD example

```javascript
const balance = 1337.23;
alert(Intl.NumberFormat('en-US', {style: 'currency', currency: 'USD' }).format(balance));
```

Result: 
```$1,337.23```

## BRL example

```javascript
const balance = 1337.23;
alert(Intl.NumberFormat('pt-BR', {style: 'currency', currency: 'BRL' }).format(balance));
```
Result: 
```R$ 1.337,23```

---