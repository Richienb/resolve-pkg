# resolve-pkg [![Build Status](https://travis-ci.org/sindresorhus/resolve-pkg.svg?branch=master)](https://travis-ci.org/sindresorhus/resolve-pkg)

> Resolve the path of a package regardless of it having an entry point

Some packages like CLI tools and grunt tasks don't have a entry point, like `"main": "foo.js"` in package.json, resulting in them not being resolvable by `require.resolve()`. Unlike `require.resolve()`, this module also resolves packages without an entry point, returns `null` instead of throwing when the module can't be found, and resolves from `process.cwd()` instead `__dirname` by default.


## Install

```
$ npm install --save resolve-pkg
```


## Usage

```js
const resolvePkg = require('resolve-pkg');

// $ npm install --save-dev grunt-svgmin

resolvePkg('grunt-svgmin/tasks', {cwd: __dirname});
//=> '/Users/sindresorhus/unicorn/node_modules/grunt-svgmin/tasks'

// Fails here as Grunt tasks usually don't have a defined main entry point
require.resolve('grunt-svgmin/tasks');
//=> Error: Cannot find module 'grunt-svgmin'
```


## API

### resolvePkg(moduleId, [options])

#### moduleId

Type: `string`

What you would use in `require()`.

#### options

##### cwd

Type: `boolean`<br>
Default: `process.cwd()`

Directory to resolve from.


## Related

- [resolve-cwd](https://github.com/sindresorhus/resolve-cwd) - Resolve the path of a module from the current working directory
- [resolve-from](https://github.com/sindresorhus/resolve-from) - Resolve the path of a module from a given path
- [import-from](https://github.com/sindresorhus/import-from) - Import a module from a given path
- [import-cwd](https://github.com/sindresorhus/import-cwd) - Import a module from the current working directory
- [import-lazy](https://github.com/sindresorhus/import-lazy) - Import a module lazily


## License

MIT © [Sindre Sorhus](https://sindresorhus.com)
