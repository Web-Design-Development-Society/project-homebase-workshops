# OXC - Oxlint & Oxfmt

See the [language support & compatability](https://oxc.rs/compatibility.html)

They have similar APIs, but you don't necessarilly have to use both of them together.

## Linting - Oxlint

```zsh
npm i -D oxlint
```

### [Configuration](https://oxc.rs/docs/guide/usage/linter/config.html)

If you want a Json based configuration, use `oxlint --init`.

If you want a TypeScript configuration, use a `oxlint.config.ts`.

```typescript
import { defineConfig } from "oxlint";

export default defineConfig({
  options: {
    typeAware: true,
    typeCheck: true,
    maxWarnings: 10,
  },
});
```

### Usage

You create scripts to lint, or run manually with `npx oxlint <file> <file>`.

```json
{
  "scripts": {
    "lint": "oxlint",
    "lint:fix": "oxlint --fix"
  }
}
```

## Formatting - Oxfmt

```zsh
npm i -D oxfmt
```

### [Confiugration](https://oxc.rs/docs/guide/usage/formatter/config.html)

If you want a Json based configuration, use `oxfmt --init`.

If you want a TypeScript configuration, use a `oxfmt.config.ts`.

```typescript
import { defineConfig } from "oxfmt";

export default defineConfig({
  printWidth: 80,
  semi: true,
  tabWidth: 2,
  sortImports: true,
});
```

### Usage

```zsh
npx oxfmt
```

Oxfmt doesn't need a `--write` flag like prettier and biome.
