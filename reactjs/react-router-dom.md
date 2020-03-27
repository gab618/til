# React Router

Today I learned how to do routing with React Router.

## Install

```npm install react-router-dom```

## Imports

```JSX
import React, { Component } from 'react';
import { BrowserRouter, Route, Switch } from 'react-router-dom';
```

## Example

```JSX
import Logon from './pages/Logon';
import Profile from './pages/Profile';

export default function Routes() {
    return (
        <BrowserRouter>
            <Switch>
                <Route path="/" exact component={Logon} />
                <Route path="/profile" component={Profile} />
            </Switch>
        </BrowserRouter>
    );
}
```
___

## \<Link\>

Provides declarative, accessible navigation around your application.

```JSX
<Link to="/register">Não tenho cadastro</Link>
```

---