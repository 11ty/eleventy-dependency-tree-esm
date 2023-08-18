# `@11ty/dependency-tree-esm`

Returns an unordered array of local paths to dependencies of a Node ES module JavaScript file.

This is used by Eleventy to find dependencies of a JavaScript file to watch for changes to re-run Eleventy’s build.

## Installation

```
npm install --save-dev @11ty/dependency-tree-esm
```

## Features

* Ignores bare specifiers (e.g. `import "my-package"`)
* Ignores Node’s built-ins (e.g. `import "path"`)
* Handles circular dependencies
* Returns an empty set if the file does not exist.

## Usage

```js
// my-file.js

// if my-local-dependency.js has dependencies, it will include those too
const test = require("./my-local-dependency.js");

// ignored, is a built-in
const path = require("path");
```

```js
const DependencyTree = require("@11ty/dependency-tree");

DependencyTree("./my-file.js");
// returns ["./my-local-dependency.js"]
```
