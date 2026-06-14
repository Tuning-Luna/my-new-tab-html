# MyNewTab — Chrome Extension New Tab Page

## Commands

```bash
npm run dev        # vite dev server (opens browser automatically)
npm run build      # type-check + vite build in parallel (via npm-run-all2)
npm run build-only # vite build only, skips type-check
npm run type-check # vue-tsc --build (validates both tsconfig.app.json + tsconfig.node.json)
npm run lint       # eslint . --fix (flat config, .vue + .ts files)
npm run preview    # vite preview of production build
```

## Build / extension quirks

- **`vite.config.ts` sets `base: './'`** — required so extension loads assets from `chrome-extension://` paths.
- **After `npm run build`, copy `manifest.json` into `dist/`** — the file lives at project root only:
  ```
  Copy-Item manifest.json dist/
  ```
- Single-entry app: `src/main.ts` → `src/App.vue`. No router, no stores.
- Path alias `@/` → `./src/` (configured in both Vite and tsconfig.app.json).

## Codebase

| Path | Notes |
|---|---|
| `src/App.vue` | Root — space background (`earch.jpg`), animated nebula + star field via CSS `radial-gradient` keyframes |
| `src/components/Logo3D.vue` | 3D Google logo with mouse-driven parallax tilt, idle floating animation, avatar with cyan ripple ring |
| `src/components/TypeWriter.vue` | Typing animation that cycles "Always Learning, Always building." |
| `eslint.config.ts` | ESLint 9 flat config (`.vue` + `.ts` files, ignores `dist/`) |
| `src/reset.css` | Global CSS reset |

## Styling
- SCSS (`lang="scss"`) used in all `.vue` files.
- `.editorconfig`: 2-space indent, LF, 100-char max line length.

## No tests
No test framework installed. Do not add or run tests without explicit user request.
