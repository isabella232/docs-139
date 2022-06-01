---
description: Facilitates the distribution of webcomponents
---

# CLI and Flags

{% embed url="https://github.com/atomicojs/exports" %}

## Flags

### --exports

You will add the build files to the exports property inside the package.json.

### --types

It requires the installation of Typescript, it will create the types and add the files to the typesVersion property inside package.json

### --analyzer

Analyze the code to generate output for third parties like react and preact

### --workspace

It will look for the subpackages that declare dependencies and it will add them in the dependencies property of the package.json

### --ignore-build

Avoid using esbuild, ideal if you have standard js code that you want to distribute without compilation

### --meta-url \<tipo de archivo>

Add additional support for files not found by [default in meta-url export](https://github.com/atomicojs/exports/blob/master/src/module.js#L23-L42).

### --main \<fileName>

Of all the exported files, it will associate the one censored with the name of the file as the main one for the export of the package.json. Main file does not require extension or path

### --dest \<destination>

Modify the destination directory for the build

### --watch

Associate the use of watch with esbuild, ignoring the type parsing and exports.

### --minify

Enables minify esbuild code.
