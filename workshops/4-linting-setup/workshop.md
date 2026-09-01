# Continuous Integration (CI) Workshop

This section will cover the **linting**, **formatting**, and the **type checking** aspect of CI. It may also cause your dev dependencies to explode.

## Instructions

Complete a workshop in some or all sections to establish better code standards. The longer you plan on working on your codebase, the more CI you should have.

Some of these CI tool chains are in development and behind in compatability. Consider this before commiting to one.

### Formatting

* [Prettier](https://prettier.io/) - Battle-tested, powerful formatter
* [Biome](https://biomejs.dev/) - Fast and opinionated
* [Oxfmt](https://oxc.rs/docs/guide/usage/formatter.html) - Fastest option, supported by Vite+

### Linting

* [ESlint](https://eslint.org/) - Battle-tested, customizabled, ecosystem-rich
* [Biome](https://biomejs.dev/) - Fast, opinionated, batteries-included
* [Oxlint](https://oxc.rs/docs/guide/usage/linter.html) - Fast and ESLint compatable

### Type Checking

* [Typechecking](./type-checking.md) - Learn how to configure type checking for your CI.

### CI Automation

Complete the [CI Automation workshop](./ci-automation.md) to establish a standard of how often you will run CI.

## Additional Resources

**Other Options**

* [Stylelint](https://github.com/stylelint/stylelint) - Linting for css
* [GPTLint](https://github.com/gptlint/gptlint) - Tell LLMs how they are bad at coding

**More CI**

These things can also be considered CI, but are not covered in this workshop.

* Testing: [Vitest](https://vitest.dev/), [Playwright](https://playwright.dev/), and more
* Static Analysis: [SonarQube](https://www.sonarsource.com/), [SemGrep](https://semgrep.dev/), [Snyk](https://snyk.io/)
* Dependency Management: [Dependabot](https://github.com/dependabot)
* Secret Scanning: [Github's Scanning](https://docs.github.com/en/code-security/concepts/secret-security/secret-scanning), [Gitleaks](https://gitleaks.io/)
