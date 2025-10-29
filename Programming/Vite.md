---
tags:
  - vite
---

#vanilla 
when createing a vanilla website with vite you need to create a vite.config.js
when you run npm run dev it will look for this file.

so when using tailwindcss file file would look like this

```javascript
import { defineConfig } from 'vite'
import tailwindcss from '@tailwindcss/vite'
export default defineConfig({
  plugins: [
    tailwindcss(),
  ],
})
```