#array.prototype.every <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![Build Status][travis-svg]][travis-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

[![browser support][testling-svg]][testling-url]

An ES5 spec-compliant `Array.prototype.every` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](http://www.ecma-international.org/ecma-262/6.0/).

Because `Array.prototype.every` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var every = require('array.prototype.every');
var assert = require('assert');

assert.equal(true, every([1, 1, 1], function (x) { return x === 1; }));
assert.equal(false, every([1, 0, 1], function (x) { return x === 1; }));
```

```js
var every = require('array.prototype.every');
var assert = require('assert');
/* when Array#every is not present */
delete Array.prototype.every;
var shimmedEvery = every.shim();
assert.equal(shimmedEvery, every.getPolyfill());
var arr = [1, 2, 3];
var lessThan4 = function (x) { return x < 4; };
assert.deepEqual(arr.every(lessThan4), every(arr, lessThan4));
```

```js
var every = require('array.prototype.every');
var assert = require('assert');
/* when Array#every is present */
var shimmedEvery = every.shim();
assert.equal(shimmedEvery, Array.prototype.every);
assert.deepEqual(arr.every(lessThan4), every(arr, lessThan4));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/array.prototype.every
[npm-version-svg]: http://versionbadg.es/ljharb/Array.prototype.every.svg
[travis-svg]: https://travis-ci.org/ljharb/Array.prototype.every.svg
[travis-url]: https://travis-ci.org/ljharb/Array.prototype.every
[deps-svg]: https://david-dm.org/ljharb/Array.prototype.every.svg
[deps-url]: https://david-dm.org/ljharb/Array.prototype.every
[dev-deps-svg]: https://david-dm.org/ljharb/Array.prototype.every/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/Array.prototype.every#info=devDependencies
[testling-svg]: https://ci.testling.com/ljharb/Array.prototype.every.png
[testling-url]: https://ci.testling.com/ljharb/Array.prototype.every
[npm-badge-png]: https://nodei.co/npm/array.prototype.every.png?downloads=true&stars=true
[license-image]: http://img.shields.io/npm/l/array.prototype.every.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/array.prototype.every.svg
[downloads-url]: http://npm-stat.com/charts.html?package=array.prototype.every
