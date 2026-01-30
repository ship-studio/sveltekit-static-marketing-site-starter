# SvelteKit Static Marketing Site Starter

A minimal SvelteKit starter with Tailwind CSS for Ship Studio projects.

## Getting Started

```bash
npm install
npm run dev
```

## Tech Stack

- **SvelteKit 2** with Svelte 5 (runes)
- **Tailwind CSS 4** via Vite plugin
- **Static adapter** for deployment to any static host
- **TypeScript** for type safety

## Project Structure

```
src/
├── routes/           # SvelteKit file-based routing
│   ├── +layout.svelte    # Root layout (wraps all pages)
│   └── +page.svelte      # Homepage
├── lib/              # Reusable components and utilities
├── app.html          # HTML template
└── app.css           # Global styles + Tailwind
static/               # Static assets (images, fonts, etc.)
```

## Deployment

This project uses the static adapter. Run `npm run build` to generate a static site in the `build/` directory.

## Ship Studio

This template is designed to work with [Ship Studio](https://shipstudio.ai), a desktop app for building marketing sites with Claude Code.
