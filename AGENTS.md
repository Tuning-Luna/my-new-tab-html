# MyNewTab — Chrome Extension New Tab Page

## Tech stack
- Vue 3 (`<script setup lang="ts">`) + TypeScript + SCSS
- Vite 7, `vue-tsc` for type checking, ESLint 9 flat config
- Chrome Extension Manifest V3

## Commands

```bash
npm run dev        # vite dev server (opens browser)
npm run build      # type-check + vite build (parallel via npm-run-all2)
npm run build-only # vite build only, no type-check
npm run type-check # vue-tsc --build
npm run lint       # eslint . --fix
npm run preview    # vite preview of production build
```

## Build / extension quirks

- **`vite.config.ts` sets `base: './'`** — required so extension loads assets from relative paths (`chrome-extension://`).
- Build output goes to `dist/`. The `manifest.json` lives at project root only. After `npm run build`, copy it into `dist/` manually for Chrome to recognize the extension:
  ```
  Copy-Item manifest.json dist/
  ```
- Single-entry app: `src/main.ts` → `src/App.vue`. No router, no stores.
- Path alias `@/` → `./src/` (configured in both Vite and tsconfig).

## Styling
- SCSS (`lang="scss"`) in `App.vue`; global reset in `src/reset.css`.
- `.editorconfig`: 2-space indent, LF, 100-char line length.

## No tests
No test framework is installed. Do not add or run tests without explicit user request.

## Notable files
| File | Purpose |
|---|---|
| `manifest.json` | Chrome extension manifest (root only) |
| `index.html` | App shell, mounts `#app` |
| `vite.config.ts` | Vite config with `@/` alias and `base: './'` |
| `eslint.config.ts` | ESLint flat config, `.vue` + `.ts` files |
