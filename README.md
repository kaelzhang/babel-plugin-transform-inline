[![Build Status](https://travis-ci.org/kaelzhang/babel-plugin-transform-inline.svg?branch=master)](https://travis-ci.org/kaelzhang/babel-plugin-transform-inline)
[![Coverage](https://codecov.io/gh/kaelzhang/babel-plugin-transform-inline/branch/master/graph/badge.svg)](https://codecov.io/gh/kaelzhang/babel-plugin-transform-inline)
<!-- optional appveyor tst
[![Windows Build Status](https://ci.appveyor.com/api/projects/status/github/kaelzhang/babel-plugin-transform-inline?branch=master&svg=true)](https://ci.appveyor.com/project/kaelzhang/babel-plugin-transform-inline)
-->
<!-- optional npm version
[![NPM version](https://badge.fury.io/js/babel-plugin-transform-inline.svg)](http://badge.fury.io/js/babel-plugin-transform-inline)
-->
<!-- optional npm downloads
[![npm module downloads per month](http://img.shields.io/npm/dm/babel-plugin-transform-inline.svg)](https://www.npmjs.org/package/babel-plugin-transform-inline)
-->
<!-- optional dependency status
[![Dependency Status](https://david-dm.org/kaelzhang/babel-plugin-transform-inline.svg)](https://david-dm.org/kaelzhang/babel-plugin-transform-inline)
-->

# babel-plugin-transform-inline

Allow inline keywords before functions and class methods.

## Install

```sh
$ npm i babel-plugin-transform-inline
```

## Usage

```js
// `inline` keyword to decorate a normal function
inline function minus (a, b) {
  return a - b
}

// Arrow function
const plus = inline (a, b) => a + b

class Foo {
  constructor (num) {
    this._num = _num
  }

  // class methods are also supported
  inline _plus (amount) {
    return plus(this._num, amount)
  }

  minus (amount) {
    return this._plus(minus(0, amount))
  }
}
```

Out:

```js
class Foo {
  constructor (num) {
    this._num = _num
  }

  minus (amount) {
    return (this._num + (0 - amount))
  }
}
```

## License

MIT
