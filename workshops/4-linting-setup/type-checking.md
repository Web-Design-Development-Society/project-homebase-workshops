# Type Checking

Decide what you want to type check. Most frameworks present type-checking diagnostics for you when you install their VS Code extensions, but you can choose to extend type checking to CI if you have strict coding standards or are using LLMs heavily.

* [Typescript Files](#checking-typescript-files)
* [Framework Files](#checking-framework-files)

## Checking Typescript Files

This is great for node projects or setups with minimal type checking. It is also used for React 19 and Solid.

```zsh
npm i -D typescript
```

Add [compile noEmit](https://www.typescriptlang.org/tsconfig/#noEmit) to your `package.json`.

```json
{
  "scripts": {
    "check-types": "tsc --noEmit"
  }
}
```

You can modify your `tsconfig.json` if you want to configure [additional things](https://www.typescriptlang.org/tsconfig/#compiler-options) to check.

## Checking Framework Files

### Astro

Astro has a [command](https://docs.astro.build/en/reference/cli-reference/#astro-check) to check types

```zsh
npx astro check
```

This installs and/or runs the Astro Type Checker.

### Svelte

Svelte has an optional [npm package](https://www.npmjs.com/package/svelte-check) they use internally in their VS Code extension, but also works as a CLI.

```zsh
npm i -D svelte-check
```

### React & Solid

TypeScript can type-check `.tsx` files, so React and Solid projects can generally use `tsc --noEmit`.

For **React**, the `tsconfig.json` configuration might use:

```json
{
  "compilerOptions": {
    "jsx": "react-jsx"
  },
}
```

Your React framework may already configure this for you.

**Solid** uses a slightly different configuration.

```json
{
  "compilerOptions": {
    "jsx": "preserve",
    "jsxImportSource": "solid-js"
  }
}
```

Solid specifically recommends this configuration because its JSX transformation is incompatible with TypeScript's JSX transformation.

> Because of these differences, it would be a _really_ bad idea to mix React and Solid in the same project.

## See Also

* React [prop-types](https://www.npmjs.com/package/prop-types) for legacy type checking