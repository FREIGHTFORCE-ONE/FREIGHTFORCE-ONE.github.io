# Agent Guidelines

## Agent Role
Webdesigner building a state of the art one page html website for a logistics company.

## Project Overview
Static one-page website. No build step. No frameworks. No JavaScript.

## Run & Test
- Open `index.html` directly in a browser.
- Verify manually. There is no test runner.

## Strict Constraints — Read Before Writing Any Code

### NO JavaScript
Do **not** write, add, or include any JavaScript whatsoever.
- No `<script>` tags
- No inline `onclick`, `onload`, or any other JS event attributes
- No theme switching, scroll detection, intersection observers, or dynamic behavior
- No external JS libraries or CDN scripts
- If a visual effect cannot be achieved in pure CSS, simplify the design instead

### NO External Dependencies
- Do not import fonts via Google Fonts `<link>` tags or `@import` from external URLs
- Do not reference any CDN, npm package, or third-party stylesheet
- Montserrat must be embedded via local `@font-face` rules using files already present in the repo, or referenced only if they exist locally
- Do not introduce any new asset files not already in the repository

## Code Style

### HTML
- Use semantic structure: `<header>`, `<main>`, `<section>`, `<footer>`
- 4-space indentation throughout
- All content in a single `index.html` file

### CSS
- All styles embedded in a single `<style>` block inside `<head>`
- Define all colors as CSS custom properties (variables) at `:root`
- Use the exact brand color values — no approximations
- Class naming: kebab-case only (e.g. `.feature-grid`, `.hero-tagline`)
- Layout: Flexbox and CSS Grid only — no floats, no absolute positioning hacks
- Animations: CSS `@keyframes` and `transition` only

## Brand Tokens (use these variable names exactly)

### Light mode (default)
```css
:root {
    --color-bg:            #FFFFFF; /* Signal White — page background */
    --color-surface:       #F5F3F4; /* Warm off-white — card surfaces */
    --color-text-primary:  #231F20; /* System Black */
    --color-text-secondary:#6B6B6B; /* Infrastructure Grey */
    --color-accent:        #2D6BE4; /* Node Blue — interactive elements & highlights */

    --font-family:         'Montserrat', sans-serif;
    --font-weight-regular:  400;
    --font-weight-semibold: 600;
}
```

### Dark mode overrides
Applied via `body:has(#theme-toggle:checked)` — no JavaScript.

```css
body:has(#theme-toggle:checked) {
    --color-bg:            #231F20; /* System Black — page background */
    --color-surface:       #161314; /* Terminal Dark — accent background / card surfaces */
    --color-text-primary:  #FFFFFF; /* Signal White */
    --color-text-secondary:#6B6B6B; /* Infrastructure Grey — unchanged */
    --color-accent:        #2D6BE4; /* Node Blue — unchanged */
}
```

## Theme Toggle
- Implemented as a hidden `<input type="checkbox" id="theme-toggle">` with a `<label>` styled as a pill switch
- No JavaScript. State is driven entirely by `:checked` + `body:has()` CSS selectors
- Toggle label lives in the header, top-right

## Assets
- Logo: `logo.svg` — use as `<img>` or inline SVG, never recreate it in CSS
<!-- - Wordmark: `wordmark.svg` — same rule -->
<!-- - Icon: `icon.svg` — same rule -->
- Do not modify SVG files
- Logo is same in dark and light mode
