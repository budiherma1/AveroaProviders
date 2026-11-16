<h1 align="center">@averoa/providers</h1>

<p align="center">
  Deprecated re-export of an AveroaJS 1.x app's <code>app/Providers</code> directory.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-deprecated-red" alt="Status: deprecated">
  <a href="https://www.npmjs.com/package/@averoa/providers"><img src="https://img.shields.io/npm/v/@averoa/providers?color=cb3837&logo=npm" alt="npm version"></a>
  <a href="#license"><img src="https://img.shields.io/badge/license-MIT-blue" alt="License: MIT"></a>
  <a href="https://github.com/budiherma1/averoajs"><img src="https://img.shields.io/badge/part%20of-AveroaJS-informational" alt="Part of AveroaJS"></a>
</p>

> **Deprecated since AveroaJS 2.0.** Do not add this package to new apps. Use the
> `#providers` subpath import instead; see [Migrating to AveroaJS 2.0](#migrating-to-averoajs-20).

## Why it was deprecated

The entire package is one line:

```js
export * from './../../../app/Providers/index.js';
```

That relative path only reaches your app when the package sits at exactly
`<your-app>/node_modules/@averoa/providers`. It breaks with pnpm, npm or Yarn workspaces,
symlinked installs (`npm link`, `file:` dependencies) and monorepos, where the
package lives somewhere else on disk.

AveroaJS 2.0 uses Node.js [subpath imports](https://nodejs.org/api/packages.html#subpath-imports)
instead. They are resolved from your app's own `package.json`, so they work however
dependencies are installed, and no extra package is needed.

## What it does today

Apps still on AveroaJS 1.x that install dependencies into a regular `node_modules`
tree can keep using this package unchanged. It forwards the named exports of
`app/Providers/index.js`; a default export is not forwarded, because `export *`
never includes `default`.

## Migrating to AveroaJS 2.0

1. Add the subpath import to your app's `package.json` (the 2.0 boilerplate already has it):

   ```json
   {
     "imports": {
       "#providers": "./app/Providers/index.js"
     }
   }
   ```

2. Update your imports:

   ```js
   // Before
   import { Something } from '@averoa/providers';

   // After
   import { Something } from '#providers';
   ```

3. Remove the dependency:

   ```bash
   npm uninstall @averoa/providers
   ```

## Related

| Project | Description |
| --- | --- |
| [averoajs](https://github.com/budiherma1/averoajs) | The AveroaJS boilerplate; the starting point for new apps (not published to npm). |
| [`@averoa/core`](https://www.npmjs.com/package/@averoa/core) ([repo](https://github.com/budiherma1/AveroaCore)) | The AveroaJS framework runtime. |

The other deprecated re-export packages, replaced the same way: [`@averoa/models`](https://github.com/budiherma1/AveroaModels), [`@averoa/repositories`](https://github.com/budiherma1/AveroaRepositories), [`@averoa/helpers`](https://github.com/budiherma1/AveroaHelpers), [`@averoa/jobs`](https://github.com/budiherma1/AveroaJobs).

## License

MIT © Budi Hermawan
