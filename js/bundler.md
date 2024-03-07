# Bundler

- Rollup
- Webpack

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
