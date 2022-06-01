# @atomico/exports

![](<../../.gitbook/assets/Grupo 2.png>)

Exporting packages through NPM for publication or use in monorepo is a really complex task, it is no longer enough to create our js, now we will have to solve minimally:

1. `compilacion`: if we want to use JS To TS, our code will largely be compiled, `@atomico/exports` uses esbuild for it
2. `package.json#exports`: declare all paths to consume from our `package.json`
3. `packages.json#types`: declares the main path of types for Typescript
4. `packages.json#typesVersions`: declare the subpaths, this is similar to package.json#exports but at the typescript level.
5. `package.json#main`: declares the main file, the main property is friendly to services like unpkg.com

**But why not automate this tedious process?** I present to you `@atomico/exports` is a tool like CLI created by Uppercod to improve the construction of packages.json frontend when talking about export.
