# Social Links

Add GitHub and LinkedIn icon links to your footer, applying what you learned in [icons.md](./icons.md).

## 1. Add Icons to Your Footer

Open your footer or layout file and add social links.

Remember update the link `href` destinations to go to your profiles.

```astro
<footer>
  <p>&copy; {new Date().getFullYear()} Your Name</p>
  <div class="social-links">
    <a href="https://github.com" target="_blank" rel="noopener noreferrer" aria-label="GitHub">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
        <path d="M16.24 22a1 1 0 0 1-1-1v-2.6a2.15 2.15 0 0 0-.54-1.66 1 1 0 0 1 .61-1.67C17.75 14.78 20 14 20 9.77a4 4 0 0 0-.67-2.22 2.75 2.75 0 0 1-.41-2.06 3.71 3.71 0 0 0 0-1.41 7.65 7.65 0 0 0-2.09 1.09 1 1 0 0 1-.84.15 10.15 10.15 0 0 0-5.52 0 1 1 0 0 1-.84-.15 7.4 7.4 0 0 0-2.11-1.09 3.52 3.52 0 0 0 0 1.41 2.84 2.84 0 0 1-.43 2.08 4.07 4.07 0 0 0-.67 2.23c0 3.89 1.88 4.93 4.7 5.29a1 1 0 0 1 .82.66 1 1 0 0 1-.21 1 2.06 2.06 0 0 0-.55 1.56V21a1 1 0 0 1-2 0v-.57a6 6 0 0 1-5.27-2.09 3.9 3.9 0 0 0-1.16-.88 1 1 0 1 1 .5-1.94 4.93 4.93 0 0 1 2 1.36c1 1 2 1.88 3.9 1.52a3.89 3.89 0 0 1 .23-1.58c-2.06-.52-5-2-5-7a6 6 0 0 1 1-3.33.85.85 0 0 0 .13-.62 5.69 5.69 0 0 1 .33-3.21 1 1 0 0 1 .63-.57c.34-.1 1.56-.3 3.87 1.2a12.16 12.16 0 0 1 5.69 0c2.31-1.5 3.53-1.31 3.86-1.2a1 1 0 0 1 .63.57 5.71 5.71 0 0 1 .33 3.22.75.75 0 0 0 .11.57 6 6 0 0 1 1 3.34c0 5.07-2.92 6.54-5 7a4.28 4.28 0 0 1 .22 1.67V21a1 1 0 0 1-.94 1z" />
      </svg>
    </a>
    <a href="https://linkedin.com" target="_blank" rel="noopener noreferrer" aria-label="LinkedIn">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
        <path d="M20 22h-1.67a2 2 0 0 1-2-2v-5.37a.92.92 0 0 0-.69-.93.84.84 0 0 0-.67.19.85.85 0 0 0-.3.65V20a2 2 0 0 1-2 2H11a2 2 0 0 1-2-2v-5.46a6.5 6.5 0 1 1 13 0V20a2 2 0 0 1-2 2zm-4.5-10.31a3.73 3.73 0 0 1 .47 0 2.91 2.91 0 0 1 2.36 2.9V20H20v-5.46a4.5 4.5 0 1 0-9 0V20h1.67v-5.46a2.85 2.85 0 0 1 2.83-2.85z" />
        <path d="M6 22H4a2 2 0 0 1-2-2V10a2 2 0 0 1 2-2h2a2 2 0 0 1 2 2v10a2 2 0 0 1-2 2zM4 10v10h2V10z" />
        <path d="M5 7a3 3 0 1 1 3-3 3 3 0 0 1-3 3zm0-4a1 1 0 1 0 1 1 1 1 0 0 0-1-1z" />
      </svg>
    </a>
  </div>
</footer>
```

> Always add `aria-label` to icon-only links for accessibility.

## 2. Style the Icons

```css
.social-links a {
  color: var(--text-color, #000);
  display: inline-flex;
  padding: 0.5rem;
  transition: color 0.2s ease, transform 0.2s ease;

  svg {
    width: 24px;
    height: 24px;
  }

  &:hover,
  &:focus-visible,
  &:active {
    color: var(--accent-color, #0077b5);
    transform: translateY(-1px);
  }
}
```

## 3. Add More Icons

Browse the icon libraries in [icons.md](./icons.md) to add more social links (e.g. Email, Facebook, X, Bluesky, YouTube). The provided SVGs are outline icons from [Eva Icons](https://akveo.github.io/eva-icons)
