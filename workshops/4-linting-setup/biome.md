# Biome

See the [language support & compatability](https://biomejs.dev/internals/language-support/)

```zsh
npm i -D -E @biomejs/biome
npx @biomejs/biome init
```

## [Configuration](https://biomejs.dev/guides/configure-biome/)

You can choose whether biome lints, formats, and/or refactors code in the `biome.jsonc`.

```json
{
  "formatter": {
    "enabled": false
  },
  "linter": {
    "enabled": false
  },
  "assist": {
    "enabled": false
  }
}
```

## [Linting](https://biomejs.dev/linter/)

```zsh
npx @biomejs/biome lint
# or
npx @biomejs/biome lint ./src ./scripts
```

## [Formatting](https://biomejs.dev/formatter/)

```zsh
npx @biomejs/biome format --write ./src
```
