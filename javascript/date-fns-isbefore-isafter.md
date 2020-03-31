# Compare dates (date-fns isBefore(), isAfter())

Today I learned how to compare dates using date-fns methods.


## Install

```npm install date-fns```

## Syntax

```javascript
isAfter(date, dateToCompare)
```

## Example

```javascript
const isAfter = require('date-fns/isAfter');
const isBefore = require('date-fns/isBefore');

// Is 10 July 1997 after 11 February 1997?
const result1 = isAfter(new Date(1997, 6, 10), new Date(1997, 1, 11));
//=> true

// Is 10 July 1997 before 11 February 1997?
const result2 = isBefore(new Date(1997, 6, 10), new Date(1997, 1, 11));
//=> false
}
```