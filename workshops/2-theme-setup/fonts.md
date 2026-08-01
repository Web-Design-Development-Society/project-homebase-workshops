# Fonts

Here is a walkthrough of a modern approach to add fonts in Astro.

## 1. Choose your fonts

This workshop includes a heading and paragraph font. If you choose your own, keep in mind it is recommended to use `sans-serif` fonts. If you want a `serif` font, use it only for headings.

Define your fonts in your `Astro.config.js`.

```typescript
export default defineConfig({
  fonts: [
    {
      provider: fontProviders.google(),
      name: "Source Sans 3",
      cssVariable: "--heading-font",
    },
    {
      provider: fontProviders.google(),
      name: "Atkinson Hyperlegible",
      cssVariable: "--paragraph-font",
    },
  ],
});
```

> [Source Sans](https://fonts.google.com/specimen/Source+Sans+3) is created by Adobe. \
> [Atkinson Hyperlegible](https://fonts.google.com/specimen/Atkinson+Hyperlegible) is a font designed by the Braille Institute of America to improve [readability for individuals with low vision](https://www.brailleinstitute.org/freefont/).

## 2. Load your fonts

You probably have your HTML `head` in `layout.astro`. Add your fonts there.

```astro
---
import { Font } from 'astro:assets';
---

<head>
  <Font cssVariable="--heading-font" preload />
  <Font cssVariable="--paragraph-font" preload />
</head>
```

Astro converts Font components to HTML `link` elements under the hood to import the fonts. Add `preload` to preload the fonts.

## 3. Use your fonts in CSS

You're done! Use your fonts anywhere in your css.

```css
body {
  font-family: var(--paragraph-font);
}

h1, h2, h3, h4, h5, h6 {
  font-family: var(--heading-font);
}
```

Astro already creates the CSS variable, so you should **NOT** add code like below. There is documentation if you'd like to add [fallbacks](https://docs.astro.build/en/guides/fonts/#customizing-font-fallbacks).

```css
/* Astro does this for you. */
:root {
  --paragraph-font: "Atkinson Hyperlegible", sans-serif;
}
```

[Additional steps](https://docs.astro.build/en/guides/fonts/#register-fonts-in-tailwind) may be required if using tailwindcss.
