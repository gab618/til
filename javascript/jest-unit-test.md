# Writing Unit Tests with Jest

Today I learned how to create unit tests with Jester.

> Jest is a delightful JavaScript Testing Framework with a focus on simplicity.

## Install

```npm install jest -D```

## Generate a basic configuration file

```npx jest --init```

## Example

Function to be tested:

```src/utils/generateUniqueId.js```

```javascript
const crypto = require('crypto');

module.exports = function generateUniqueId() {
    return crypto.randomBytes(4).toString('HEX');
}
```

Unit test for the function:

```tests/unit/generateUniqueId.spec.js```

```javascript
const generateUniqueId = require('../../src/utils/generateUniqueId');
describe('Generate unique ID', () => {
    it('should generate a 8 characteres ID', () => {
        const id = generateUniqueId();
        expect(id).toHaveLength(8);
    });
});
```
## Running tests

```npm test```


