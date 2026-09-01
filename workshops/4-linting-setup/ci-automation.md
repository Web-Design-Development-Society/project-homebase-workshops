# CI Automation

After you set up your automation, the question is: When are you going to run it? Pick one or a mix of both.

* [During Deployment](#during-deployment)
* [During Development](#during-development)

Some prefer during development so they can catch warnings earlier. Some complain they lose their flow and want linting only to be done in deployment pipelines.

## During Deployment

You can choose to fail your deployment if linting or type checking doesn't pass. Add these steps to your deploy script.

```yaml
- name: Lint
  run: npm run lint
- name: Type Check
  run: npm run check-types
```

Linting and Typechecking can take a long time on large code bases or slow computers. Deeper checks are best done in deployment.

## During Development

You or your AI coding assistents may randomly decide to run your CI scripts, but you can guarentee it using **git hooks**.

For Web Development projects, [Husky 🐶](https://typicode.github.io/husky/) and [Lint-Staged 🚫💩](https://www.npmjs.com/package/lint-staged) are a great combo.

You'll need to decide when you run each part of your CI. This example will lint & format during pre-commit and type-check during pre-push.

### Lint Staged Setup

This is a tool specifically for pre-commits. If you're not using them, you don't need this package.

```zsh
npm i -D lint-staged
```

Create a `lint-staged.config.cjs` file. Choose which file extensions get linted, and which are only formatted.

```javascript
const joinFiles = (files) => files.map((file) => `"${file}"`).join(" ");

module.exports = {
  "*.{ts,js,cjs,astro}": (stagedFiles) => {
    const files = joinFiles(stagedFiles);
    return [
      `prettier --write ${files}`,
      `eslint --max-warnings=0 ${files}`
    ];
  },
  "*.{md,css}": (stagedFiles) => [
    `prettier --write ${joinFiles(stagedFiles)}`,
  ],
};
```

### Husky Setup

Husky allows you to version control and share your [git hooks](https://git-scm.com/book/ms/v2/Customizing-Git-Git-Hooks).

**Install and prepare Husky**

```zsh
npm i -D husky
npx husky init
```

You'll see this script added to your package.json. It runs commands to modify files inside the `.git` folder to set up your git hooks.

```json
{
  "scripts": {
    "prepare": "husky"
  },
}
```

_If you run into issues in a monorepo, you can replace the [prepare](https://github.com/alexanderdombroski/sleep-outside/blob/main/package.json#L13) with a [custom script](https://github.com/alexanderdombroski/sleep-outside/blob/main/.husky/prepare.ts) such as in this repository._

**Define your git hooks**

pre-commit

```bash
#!/usr/bin/env sh
npx lint-staged
```

pre-push

```bash
#!/usr/bin/env sh
npm run check-types
```

The shebangs are cool but optional. Git hooks can be skipped with `--no-verify` if you use the git cli.
