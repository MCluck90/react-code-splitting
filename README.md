# react-code-splitting

You're working on a great app powered by React, bundled with webpack and your bundle size increases ... You're in the right place to solve this modern JS apps nightmare.


## Prerequisite

- You're using [Webpack 2](https://webpack.js.org/)
- You've polyfilled ***Promise*** to support old browser

## How-to

#### Without code splitting

`<Login />` + `<Home />` are loaded at the first start
```jsx
import Login from './Login'
import Home from './Home'

const App = ({ user }) => (
  <Body>
    {user.loggedIn ? <Route path="/" component={Home} /> : <Redirect to="/login" />}
    <Route path="/login" component={Login} />
  </Body>
)
```

#### With code splitting

You're not logged in ? `<Login />` component is the only loaded, `<Home />` will be loaded when the user will be logged in.
```jsx
import Async from 'react-code-splitting'

import Login from './Login'
const Home = () => <Async load={import('./Home')} />

const App = ({ user }) => (
  <Body>
    {user.loggedIn ? <Route path="/" component={Home} /> : <Redirect to="/login" />}
    <Route path="/login" component={Login} />
  </Body>
)
```

You can view this snippets in context [here](https://github.com/didierfranc/redux-react-starter/blob/master/src/components/App.js#L11) !

## More

Webpack examples with some code splitting techniques https://github.com/webpack/webpack/tree/master/examples