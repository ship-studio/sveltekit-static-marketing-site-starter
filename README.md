# SvelteKit Static Marketing Site Starter

A minimal, well-configured SvelteKit starter for building marketing sites with Claude Code via Ship Studio.

## Quick Start

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Open http://localhost:5173
```

## Tech Stack

- **SvelteKit 2** - Full-stack framework with file-based routing
- **Svelte 5** - Uses runes (`$state`, `$props`, `$derived`, `$effect`)
- **Tailwind CSS 4** - Utility-first CSS via Vite plugin
- **TypeScript** - Full type safety
- **Static Adapter** - Generates static HTML for any hosting platform

## Project Structure

```
src/
├── routes/                  # Pages (file-based routing)
│   ├── +layout.svelte       # Root layout (wraps all pages)
│   ├── +layout.ts           # Prerender config
│   └── +page.svelte         # Homepage (yoursite.com/)
├── lib/                     # Reusable code
│   ├── components/          # UI components
│   │   └── Button.svelte    # Example component
│   └── index.ts             # Barrel exports
├── app.css                  # Global styles + design tokens
├── app.d.ts                 # TypeScript declarations
└── app.html                 # HTML template

static/                      # Static assets (images, fonts)
.claude/                     # Claude Code skills and settings
```

## Design System

The design tokens in `src/app.css` define your site's visual identity:

```css
:root {
	/* Colors */
	--background: #fafaf9;
	--foreground: #1c1917;
	--muted: #78716c;
	--accent: #dc2626;

	/* Typography */
	--font-display: 'Space Grotesk', sans-serif;
	--font-body: 'DM Sans', sans-serif;
}
```

Use them in Tailwind classes: `bg-background`, `text-foreground`, `text-muted`, `text-accent`, `font-display`

## Adding Pages

Create a new folder in `src/routes/` with a `+page.svelte` file:

```
src/routes/about/+page.svelte  →  yoursite.com/about
src/routes/pricing/+page.svelte  →  yoursite.com/pricing
```

## Available Scripts

| Command           | Description                                |
| ----------------- | ------------------------------------------ |
| `npm run dev`     | Start dev server at localhost:5173         |
| `npm run build`   | Build for production (outputs to `build/`) |
| `npm run preview` | Preview production build locally           |
| `npm run check`   | Run TypeScript and Svelte checks           |
| `npm run format`  | Format code with Prettier                  |

## Deployment

This project generates static HTML. Deploy the `build/` folder to any static host:

- **Vercel**: Zero-config, just connect your repo
- **Netlify**: Zero-config, just connect your repo
- **Cloudflare Pages**: Zero-config, just connect your repo
- **GitHub Pages**: Set output directory to `build`

## Ship Studio Integration

This starter is designed for [Ship Studio](https://shipstudio.ai), which provides:

- **Onboarding** (`/onboarding`) - Guided project setup
- **Page Remake** (`/page-remake`) - Rebuild sites from URL examples
- **Sanity CMS** (`/sanity-cms`) - Add editable content

Claude Code skills in `.claude/skills/` provide specialized guidance for design, copywriting, animations, and more.

## VS Code Setup

Recommended extensions are configured in `.vscode/extensions.json`:

- Svelte for VS Code
- Tailwind CSS IntelliSense
- Prettier

## License

MIT
