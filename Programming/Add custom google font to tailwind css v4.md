---
tags:
  - css
  - tailwind
  - fonts
---
<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>


# How to Add Roboto Font to Tailwind CSS v4 (No Config File)

**With Tailwind v4, you can use Google Fonts with the new CSS-only workflow.**

## 1. Import Roboto Font in Your CSS

Place this at the very top of your CSS file (before importing Tailwind):

```css
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');
@import "tailwindcss";
```


## 2. Register Roboto Using the `@theme` Directive

Add this below your imports in the same CSS file:

```css
@theme {
  --font-roboto: "Roboto", sans-serif;
}
```


## 3. Use the Roboto Font Utility in Your HTML

Simply use the utility class in your markup:

```html
<div class="font-roboto">
  This uses Roboto!
</div>
```

**That’s it!** No `tailwind.config.js` needed. This workflow is compatible with Tailwind CSS v4 and works great with tools like Obsidian for note-taking.

***

Copy the text above into a `.md` file and you can reference it in Obsidian anytime!

