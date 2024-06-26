# Bundler

- Rollup
- Webpack
- tsc
- babel

## Rollup & Webpack

- "Use webpack for apps, and Rollup for libraries"
- Webpack better for commonjs
- Rollup better for ES module

## Format

- iife (browser)
- cjs (nodejs)
  - CommonJS: `require` `module.export`
  - default in nodejs
- umd (nodejs & browser)
  - works everywhere and usually used as a fallback in case ESM does not work
- es: `import` `export`
  - standard for Javascript
  - is the best module format thanks to its simple syntax, async nature, and tree-shakeability
- amd
  - asynchronous and good for front end.
- https://github.com/rollup/awesome?tab=readme-ov-file#modules

### Why ES Module better than CommonJS

- Optimizations with
  - Tree-shaking
  - Scope-hoisting
- Advance feature
  - Circular references
  - Live bindings

# Rollup

## Configuration (`rollup.config.js`)

- https://rollupjs.org/configuration-options/

## Plugins

- Building hooks
- List of plugins: https://github.com/rollup/awesome

# Babel

- Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backwards compatible version of JavaScript in current and older browsers or environments
  - Transform syntax
  - Polyfill features

# tsdx

- zero config for typescript library
- include react

# vite
