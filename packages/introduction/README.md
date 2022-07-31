# @atomico/exports

{% hint style="info" %}
`@atomico/exports` is distributed as ESM, so your `package.json` must define the property `"type":"module"` for its use.
{% endhint %}

![](<../../.gitbook/assets/Grupo 2.png>)

Exporting packages through NPM for publication or use in monorepo is a really complex task, it is no longer enough to create our js, now we will have to solve minimally:

1. `compilacion`: if we want to use JS To TS, our code will largely be compiled, `@atomico/exports` uses esbuild for it
2. `package.json#exports`: declare all paths to consume from our `package.json`
3. `packages.json#types`: declares the main path of types for Typescript
4. `packages.json#typesVersions`: declare the subpaths, this is similar to package.json#exports but at the typescript level.
5. `package.json#main`: declares the main file, the main property is friendly to services like unpkg.com

**But why not automate this tedious process?** I present to you `@atomico/exports` is a tool like CLI created by Uppercod to improve the construction of packages.json frontend when talking about export.

## With @atomico/exports you can get:

### Export and compile your code using expressions

```bash
exports ./src/*.{js,ts}
```

The expression `./src/*.{js,ts}` defines that all js and ts type files are exported inside the src folder, the exported files will be compiled thanks to **Esbuild**.

### Aesthetic import.

```js
import moduleA from "module/dist/a.js"; // ❌
import moduleA from "module/a"; // ✅
```

`@atomico/exports` will allow you to use exports as module/a, since it internally creates the `exports` and `typesVersions` properties within the package.json, to resolve this export you must use the following command:

```bash
exports ./src/*.{js,ts} --exports --types
```

remember that `./src/*.{js,ts}` is just an expression, it can be modified with your file path.

### watch mode

The purpose of `@atomico/exports` is to create the output files and associate them correctly with the package.json, the result is a modified package.json. the `--watch` flag, allows you to modify your package.json but temporarily, this is ideal for monorepos that automate their publication through automation flows, you will keep a clean package in development that will only be decorated in production.

```bash
exports ./src/*.{js,ts} --exports --types --watch
```

The --types flag requires Typescript as a devDependency

## Installation

{% tabs %}
{% tab title="NPM" %}
```bash
npm install -D @atomico/exports
```
{% endtab %}

{% tab title="package.json#scripts" %}
```javascript
{
 /**
  * ⚠️ The --types flag requires the installation of @typescript
  */
 "scripts": {
   "exports": "exports src/components/*/*.js --exports --watch"
 }
}
```
{% endtab %}
{% endtabs %}

