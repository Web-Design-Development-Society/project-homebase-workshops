# ESLint

The configuration for [eslint](https://eslint.org/) can feel endless, but here is a good starting point.

With a flat config, you can add as many modules as you want and keep everything separated and layered by file pattern.

## Configuration

Start with an minimal `eslint.config.mts`.

> You can try out the `npm init @eslint/config@latest` command too.

```zsh
npm i -D eslint typescript-eslint globals @eslint/js
```

```typescript
import js from "@eslint/js";
import globals from "globals";
import ts from "typescript-eslint";
import { defineConfig } from "eslint/config";

export default defineConfig([
  {
    files: ["**/*.{js,mjs,cjs,ts,mts,cts}"],
    plugins: { js },
    extends: ["js/recommended"],
    languageOptions: { globals: globals.browser },
  },
  ts.configs.recommended,
]);
```

### Additional Rules

You can turn on and off specific rules. I like adding these ones.

```typescript
export default defineConfig([
  {
    ignores: ['**/node_modules/**', '**/dist/**', '**/.astro/**'],
  },
  // previous config options
  {
    rules: {
      eqeqeq: 'warn',
      semi: 'warn',
      '@typescript-eslint/consistent-type-imports': 'warn',
      '@typescript-eslint/no-unused-vars': 'warn',
    },
  },
  {
    files: ['scripts/**/*.{ts,js}'],
    languageOptions: {
      globals: globals.node,
    },
  },
]);
```

## Usage

```zsh
npx eslint .
# or
npx eslint ./src ./scripts
```

## See Also

* [Configure Plugins Guide](https://eslint.org/docs/latest/use/configure/plugins)
* [Awesome Plugins List](https://github.com/dustinspecker/awesome-eslint)
