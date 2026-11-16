<h1 align="center">@averoa/providers</h1>

<p align="center">
  <img src="https://img.shields.io/badge/status-deprecated-red.svg" alt="Deprecated">
  <a href="https://www.npmjs.com/package/@averoa/providers"><img src="https://img.shields.io/npm/v/@averoa/providers?color=cb3837&logo=npm" alt="npm version"></a>
  <img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="License: MIT">
</p>

<p align="center">
  ⚠️ <b>Deprecated since AveroaJS 2.0.</b> Do not add this package to new apps.<br>
  Use the <code>#providers</code> subpath import of the
  <a href="https://github.com/budiherma1/averoajs">AveroaJS boilerplate</a> instead.
</p>

---

This package only re-exported your app's `app/Providers/index.js` through a fixed
relative path (`./../../../app/Providers/index.js`). That only works when the package is
installed at exactly `node_modules/@averoa/providers`, and it breaks with pnpm,
npm workspaces, symlinked installs and monorepos.

## Migrating to AveroaJS 2.0

Add a subpath import to your app's `package.json` (the 2.0 boilerplate already has it):

```json
{
  "imports": {
    "#providers": "./app/Providers/index.js"
  }
}
```

Then replace

```js
import { Something } from '@averoa/providers';
```

with

```js
import { Something } from '#providers';
```

and remove `@averoa/providers` from your dependencies.

Apps still on AveroaJS 1.x can keep using this package unchanged.
