# JWT Authentication

Today I learned how to use ```jsonwebtoken``` for JWT authentication.

## Installation

```bash
$ yarn add jsonwebtoken
```

## Usage

```javascript
jwt.sign(payload, secretOrPrivateKey, [options, callback]);
```

## Example

A very simple validation expects my username and 'superSecretPassword' password. It will return a valid token to my ID that expires in 7 days.

```js
const express = require('express');
const jwt = require('jsonwebtoken');

const app = express();
app.use(express.json());

app.post('/sessions', (req, res) => {
    const {id, username, password } = req.body;

    if( username !== 'gab618' || password !== 'superSecretPassword'){
        return res.status(401).json({error: 'You have failed'});
    }
    return res.json({
        user:username,
        token: jwt.sign({ id }, 'JWT_SECRET', {expiresIn: '7d'}),
    });
});

app.listen(3000);
```