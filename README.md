> [🇨🇳 中文版](README-cn.md)

# MyNewTab — Chrome Extension New Tab Page

A minimal, aesthetic new tab page for Chrome, featuring a space-themed 3D interactive landing page.

Built with **Vue 3** + **TypeScript** + **SCSS**, powered by **Vite 7**.

## Features

- **Space-themed background** — Earth photo with animated nebula and star field
- **3D Google logo** — Interactive parallax tilt that follows mouse movement, with idle floating animation and neon glow on hover
- **Avatar with ring animation** — Pulsing cyan ripple effect
- **TypeWriter animation** — Cycles "Always Learning, Always building." with a typing/timing loop
- Click the Google logo to navigate to Google

## Usage (Extension)

1. Build the project:
   ```bash
   npm run build
   ```
2. Copy `manifest.json` into `dist/`:
   ```bash
   Copy-Item manifest.json dist/
   ```
3. Open Chrome → `chrome://extensions` → enable Developer mode → **Load unpacked** → select `dist/`

## Development

```bash
# Install dependencies
npm i

# Dev server (opens browser)
npm run dev

# Type check
npm run type-check

# Lint & fix
npm run lint

# Production build (type-check + vite build)
npm run build
```

## Tech Stack

| Tool | Purpose |
|---|---|
| Vue 3 `<script setup>` | Component framework |
| TypeScript | Type safety |
| SCSS | Scoped styling |
| Vite 7 | Build tool, `base: './'` for extension |
| vue-tsc | Type checking |
| ESLint 9 flat config | Linting |
| Chrome Extension MV3 | `chrome_url_overrides: { newtab }` |

## Project Structure

```
src/
├── main.ts              # Entry point
├── App.vue              # Root — space background, nebula, stars
├── reset.css            # Global CSS reset
├── components/
│   ├── Logo3D.vue       # 3D Google logo + avatar with ring
│   └── TypeWriter.vue   # Typing animation
└── assets/
    ├── earch.jpg        # Earth background
    ├── google_logo.svg  # Google logo
    └── Tuning.png       # Avatar image
```

## Snapshots

The Earth background, Google logo, and avatar can be swapped by replacing files in `src/assets/`.
