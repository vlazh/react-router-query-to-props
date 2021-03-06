# react-router-query-to-props [![npm package](https://img.shields.io/npm/v/react-router-query-to-props.svg?style=flat-square)](https://www.npmjs.org/package/react-router-query-to-props)

React higher-order component which provide location query as props to target component. For parsing location query it uses [qs](https://github.com/ljharb/qs).

## Installation

```sh
yarn add react react-router react-router-query-to-props
# or
npm install --save react react-router react-router-query-to-props
```

## Usage

```js
// location: http://localhost:8008/myapp?param1=1&param2=2

import React from 'react';
import queryToProps from 'react-router-query-to-props';

@queryToProps()
class MyComponent extends React.Component {
  render() {
    // You can access to location query through this.props.query.
    const { query } = this.props;
    // query.param1
    // query.param2

    return (...)
  }
}
```

## Options

**queryToProps** can accept an options object:
```js
function transformer({ param1, param2, ...rest } = {}) {
  return {
    param1: param1 ? +param1 : undefined,
    param2: param2 ? +param2 : undefined,
    ...rest
  };
}

@queryToProps({ includeMatchParams: true, transform: transformer })
class MyComponent extends React.Component {
...
```

Name | Type | Description
--- | --- | ---
`includeMatchParams` | `boolean` | Include match params of [react-router](https://github.com/ReactTraining/react-router) to query object.
`transform` | `(queryObject: Record<string, any>) => any` | function that can transform query object as you need. For example, convert types. Accept raw query object as single parameter.
all options of [qs](https://github.com/ljharb/qs) | |

## License

[MIT](https://opensource.org/licenses/mit-license.php)
