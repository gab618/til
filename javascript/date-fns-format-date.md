# Format dates

Today I learned how to format dates using date-fns.

> Return the formatted date string in the given format.

## Install

```npm install date-fns```

## Syntax

```javascript
isAfter(date, dateToCompare)
```

## Accepted tokens

| Unit        | Token           | Result  |
| ------------- |:-------------:| -----:|
| Month | MM | 1, 2, ..., 12 |
| Day | dd | 1, 2, ..., 31 |
| Year | YYYY | 00, 01, 02, ..., 2048 |
| Hour | H | 0, 1, ... 23 |
| Minute | mm | 00, 01, ..., 59 |

The characters wrapped in square brackets are escaped.
The result may vary by locale.

[All tokens](https://date-fns.org/v1.30.1/docs/format)

## Example

```javascript
const date = new Date(1997,6, 10, 4, 4, 0, 0);
const formatedDate = format(date, "'Dia' dd 'de' MMMM 'de' yyyy 'às' H'h'mm", {
        locale: pt,
      });
//=> Dia 10 de julho de 1997 as 4h04
```

