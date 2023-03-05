# Configuration mapping from webpack to rspack

[Webpack](https://webpack.js.org/) is an outstanding project that has been developed over many years and supports the building of thousands of web applications.

[Rspack](https://www.rspack.dev/) is a new project that is dedicated to faster web application builds while also being compatible with the webpack ecosystem.

> This is not an official documentation and accuracy is not guaranteed. Only intended for developers as a reference. The rspack team may provide official documentation.

> Based on webpack 5.

> ✅: support
>
> ❌: not support
>
> ⚠️: partially support

## Entry

### string ✅

### string[] ✅

### EntryObject ⚠️

- import: EntryItem; ✅
- runtime?: string | false; ✅
- others ❌

### Function ❌

- (() => string | EntryObject | string[] | Promise<EntryStatic>) ❌

## Context ✅

## Mode ✅

## Output

### Output.assetModuleFilename ⚠️

- string ✅
- ((pathData: PathData, assetInfo?: AssetInfo) => string) ❌

### Output.filename ⚠️

- string ✅
- ((pathData: PathData, assetInfo?: AssetInfo) => string) ❌

### Output.chunkFilename ⚠️

- string ✅
- ((pathData: PathData, assetInfo?: AssetInfo) => string) ❌

### Output.cssFilename ⚠️

- string ✅
- ((pathData: PathData, assetInfo?: AssetInfo) => string) ❌

### Output.cssChunkFilename ⚠️

- string ✅
- ((pathData: PathData, assetInfo?: AssetInfo) => string) ❌

### Output.path ✅

- string

### Output.publicPath ⚠️

- string ✅
- ((pathData: PathData, assetInfo?: AssetInfo) => string) ❌

### Output.strictModuleErrorHandling ✅

- boolean

### Output.[...others] ❌

### Template strings ⚠️

#### Compilation-level ⚠️

- [fullhash] ✅
- [hash] ❌

#### Chunk-level ✅

- [id] ✅
- [name] ✅
- [chunkhash] ✅
- [contenthash] ✅

#### Module-level ⚠️

- [id] ✅
- [moduleid] ❌
- [hash] ✅
- [modulehash] ❌
- [contenthash] ✅

#### File-level ⚠️

- [file] ❌
- [query] ✅
- [fragment] ❌
- [base] ❌
- [filebase] ❌
- [path] ✅
- [name] ✅
- [ext] ✅

#### URL-level ❌

- [url] ❌

## Module

### Module.generator ❌

### Module.parser ⚠️

### Rule

#### Rule Condition ⚠️

- string ✅
- RegExp ✅
- function ❌

#### Rule.exclude ✅

#### Rule.include ✅

#### Rule.loaders ✅

Prefer to `Rule.use`

#### Rule.parse ✅

- dataUrlCondition ✅

#### Rule.generator ⚠️

- filename ✅
- dataUrl ❌
- emit ❌
- publicPath ❌
- outputPath ❌

#### Rule.resource ✅

#### Rule.resourceQuery ✅

#### Rule.sideEffects ✅

#### Rule.test ✅

#### Rule.type ⚠️

- asset/resource ✅
- asset/inline ✅
- asset/source ✅
- asset ✅

Other types supported by Rspack:

- javascript/auto
- typescript
- css
- css/module
- json

#### Rule.use ⚠️

- useEntry ✅
- function ❌

#### Rule.resolve ⚠️

#### Rule.[...others] ❌

## Resolve

### Resolve.alias ✅

### Resolve.aliasField ⚠️

The types of this configuration are different:

- webpack: `string[]`
- Rspack: `Boolean`

### Resolve.conditionNames ✅

### Resolve.extensions ⚠️

Default value are diffrent:

- webpack: `['.js', '.json', '.wasm']`
- rspack: `['.tsx', '.jsx', '.ts', '.js', '.json', '.d.ts']`

### Resolve.fallback ✅

### Resolve.mainFields ✅

### Resolve.mainFiles ✅

### Resolve.modules ✅

### Resolve.preferRelative ✅

### Resolve.[...Others] ❌

## Optimization

### Optimization.moduleIds ⚠️

- natural ❌
- named ✅
- deterministic ✅
- size ❌

### Optimization.minimize ✅

### Optimization.minimizer ⚠️ ???

- plugins[] ✅
- function ❌

### Optimization.removeAvailableModules ⚠️

Default value are different:

- webpack: only `true` in production mode
- rspack: always `true`

### Optimization.removeEmptyChunks ✅

### Optimization.runtimeChunk ⚠️

- object ❌
- string ❌
- boolean ✅

### Optimization.sideEffects ✅

### Optimization.splitChunks ⚠️

_This is truly amazing, their default configurations are completely identical._

#### splitChunks.automaticNameDelimiter ✅

#### splitChunks.chunks ✅

#### splitChunks.maxAsyncRequests ✅

#### splitChunks.maxInitialRequests ✅

#### splitChunks.defaultSizeTypes ✅

#### splitChunks.minChunks ✅

#### splitChunks.hidePathInfo

#### splitChunks.minSize ⚠️

- number ✅
- object ❌

#### splitChunks.minSizeReduction ⚠️

- number ✅
- object ❌

#### splitChunks.enforceSizeThreshold ✅

#### splitChunks.minRemainingSize ✅

#### splitChunks.layer ❌

#### splitChunks.maxSize ✅

#### splitChunks.maxAsyncSize ✅

#### splitChunks.maxInitialSize ✅

#### splitChunks.name ✅

#### splitChunks.usedExports ❌

#### splitChunks.cacheGroups ⚠️

## Plugins

> - Some plugins can be replaced by built-in features, refer to [this list](https://www.rspack.dev/guide/plugin-compat.html).
> - Custom plugin apis : https://www.rspack.dev/api/plugin-api.html

### DefinePlugin ✅

use `builtins.define`

### [tsconfig-paths-webpack-plugin](https://www.npmjs.com/package/tsconfig-paths-webpack-plugin)

use `resolve.tsConfigPath`

```js
module.exports = {
  resolve: {
    tsConfigPath: true,
  },
};
```

## Loaders

> - https://www.rspack.dev/guide/loader-compat.html

## DevServer ⚠️

// todo

## Cache ❌

rspack only supports setting to boolean values.

## Devtool ✅

## Target ⚠️

- async-node[[X].Y] ❌
- electron[[X].Y]-main ❌
- electron[[X].Y]-renderer ❌
- electron[[X].Y]-preload ❌
- node[[X].Y] ⚠️
  - `node`
- node-webkit[[X].Y] ❌
- nwjs[[X].Y] ❌
- web ✅
- webworker ⚠️
  - Rename to `web-worker`
- esX ✅
- browserslist ✅

## Watch and WatchOptions ❌

## Externals ⚠️

- string ❌
- object ✅
- function ❌
- RegExp ❌
- [] ❌

## **Performance** ❌

## Node ❌

use `resolve.fallback`

## Stats ⚠️

// todo

## Experiments ❌

Although both have the `experiments` configuration option, the experimental features of webpack and rspack are completely different, so do not configure webpack's experimental features in rspack.
