universal-env
================

[![Build Status][travis-image]][travis-url]
[![Coverage Status][coveralls-image]][coveralls-url]
[![NPM version][npm-version-image]][npm-url]
[![NPM downloads][npm-downloads-image]][npm-url]
[![MIT License][license-image]][license-url]

[![Sauce Test Status][saucelabs-image]][saucelabs-url]

>Standard environment definition, utilities and constants for browser and node JavaScript applications

# Introduction

This package provides utilities for working with environment configuration consistently in different runtimes via configuration objects or environment variables.

We created this at [WeWork](https://www.wework.com) to provide our applications a more consistent runtime. We use it with tools like `dotenv` and `webpack` in universal JavaScript applications.

# Usage

See the [documentation](./API.md). Note that most util functions expect to receive `process.env` when not calling the root `env` function.

This package is bundled as a CommonJS module in `dist` and can be required like any other. The ES2015 source is also exposed via the [`jsnext:main` field in the `package.json`](https://github.com/rollup/rollup/wiki/jsnext:main) for loaders that support module syntax directly.

## Webpack

`utils.getPublicEnv` is very handy to safely expose environment config for a client bundle. See [docs for getPublicEnv](./API.md#getpublicenv), and our own use of it in [`test/browser/webpack.config.js`](./test/browser/webpack.config.js).

## Examples

```js
import getEnv from 'universal-env';
const env = getEnv();

console.log(env.version);
console.log(env.is.client);
console.log(env.is.server);
console.log(env.is.prod);
console.log(env.is.dev);
```

# Development

1. Checkout this repo
2. Run `npm install`
3. Make changes in a feature branch and open a PR to `master`

In lieu of a formal style guide, please:

 - follow the conventions present in the codebase
 - respect the linter
 - keep tests green
 - maintain test coverage

# npm scripts

### npm scripts

Target | Behavior
------------ | -------------
**`npm test`** | Runs tests in browser and node runtimes
**`npm run tdd`** | Runs tests, bundles and re-runs on file changes
**`npm run test:coverage`** | Runs tests and outputs a code coverage report to `/coverage`
**`npm run test:ci`** | Runs tests, outputs code coverage and JUnit reports
**`npm run lint`** | (*Run as a git pre-commit hook*) Runs `eslint`
**`npm run docs`** | Generates `API.md` from JSDoc comments in `/src`
**`npm run security-scan`** | (*Run as a git pre-push hook*) Checks npm dependencies for security vulnerabilities
**`npm run release <version>`** | Generates a changelog, updates package version, tags and pushes via [`np`](https://www.npmjs.com/package/np). This should only be run on an up-to-date `master` by a maintainer of this package. <br /><br />Version can be a semver level: `patch | minor | major | prepatch | preminor | premajor | prerelease`, or a valid semver version: `1.2.3`.

**`npm run` will list all npm scripts**


[npm-url]: https://npmjs.org/package/universal-env
[npm-version-image]: http://img.shields.io/npm/v/universal-env.svg?style=flat-square
[npm-downloads-image]: http://img.shields.io/npm/dm/universal-env.svg?style=flat-square

[coveralls-image]:https://coveralls.io/repos/github/wework/universal-env/badge.svg?branch=master
[coveralls-url]:https://coveralls.io/github/wework/universal-env?branch=master

[travis-url]:https://travis-ci.org/wework/universal-env
[travis-image]: https://travis-ci.org/wework/universal-env.svg?branch=master

[saucelabs-image]:https://saucelabs.com/browser-matrix/universal-env.svg
[saucelabs-url]:https://saucelabs.com/u/universal-env

[license-url]: LICENSE
[license-image]: http://img.shields.io/badge/license-MIT-000000.svg?style=flat-square
