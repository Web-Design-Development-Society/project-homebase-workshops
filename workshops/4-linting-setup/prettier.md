# Prettier

Prettier will format everything. You don't have to worry about a teammates odd choice of indentation.

```zsh
npm i -D prettier
```

Create a `.prettierc` configuration.

```json
{
  "semi": true,
  "singleQuote": false,
  "tabWidth": 2,
  "useTabs": false,
  "printWidth": 100,
  "trailingComma": "es5",
  "arrowParens": "always"
}
```

Try it!

```zsh
npx prettier --write src
```

## Plugins

If you only format through the [VS Code extension](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode), many of these come bundled and you don't need to install them.

**Astro** - [prettier-plugin-astro](https://github.com/withastro/prettier-plugin-astro)

```zsh
npm i -D prettier-plugin-astro
```

```json
{
  "plugins": ["prettier-plugin-astro"],
  "overrides": [
    {
      "files": "*.astro",
      "options": {
        "parser": "astro"
      }
    }
  ]
}
```

Every single plugin you will need to add to your `.prettierrc` entries that look similar to this

**Svelte** - [prettier-plugin-svelte](https://github.com/sveltejs/prettier-plugin-svelte)

```zsh
npm i -D prettier-plugin-svelte
```

**SQL, Postgres, and other variants**

```zsh
npm i -D prettier-plugin-sql-cst
```

## See also

* [.prettierignore](https://prettier.io/docs/ignore#ignoring-files-prettierignore) - Don't format specific file patterns
* List of [all plugins](https://prettier.io/docs/plugins#official-plugins)
