# Ship Studio Project

This is a SvelteKit 2 project with Svelte 5 and Tailwind CSS. You're helping a **non-developer** build a website. Keep explanations simple and jargon-free.

---

## Environment: Ship Studio App

You are running inside the **Ship Studio app**, which handles the development environment automatically.

**Important things to know:**

- The dev server is **already running** - you don't need to start it
- The user sees a live preview of their site in the app
- You don't need to run `npm run dev` or any server commands
- Changes to files are reflected automatically in the preview

**If the user says they can't see their site or the preview isn't working:**

> "Try clicking the **Projects** button in the top right corner to go back to the project list, then reopen your project. This restarts the preview."

---

## FIRST: Check for Onboarding

**Before doing anything else**, check if `SITE.md` exists.

- If `SITE.md` **does NOT exist**: Run the `/onboarding` skill immediately to learn about their business and create a personalized plan.
- If `SITE.md` **exists**: Read it to understand the project before making changes.

---

## Your Skills

You have specialized skills in `.claude/skills/`. **Use them constantly:**

| Skill                       | When to Use                                  | Invocable      |
| --------------------------- | -------------------------------------------- | -------------- |
| **onboarding**              | New project setup, no SITE.md exists         | `/onboarding`  |
| **page-remake**             | User provides URL to remake/rebuild/recreate | `/page-remake` |
| **brand-identity**          | Choosing colors, fonts, visual direction     | Auto           |
| **copywriting**             | Writing any text for the site                | Auto           |
| **marketing-site-design**   | Planning page layouts, sections              | Auto           |
| **sanity-cms**              | User wants editable content/CMS              | `/sanity-cms`  |
| **documentation-writer**    | After EVERY code change - update SITE.md     | Auto           |
| **svelte-sveltekit-expert** | Writing any Svelte/SvelteKit code            | Auto           |
| **svelte-code-writer**      | Svelte MCP tools for docs & code validation  | Auto           |
| **frontend-design**         | Creating any visual component                | Auto           |
| **animations**              | Adding micro-interactions and motion         | Auto           |
| **svelte-best-practices**   | Performance optimization                     | Auto           |

### Workflow for Every Build Task

1. Check `SITE.md` for brand personality and preferences
2. Use `marketing-site-design` to plan section architecture
3. Use `brand-identity` to select colors/fonts (follow design principles)
4. Use `copywriting` to write specific, human-sounding text
5. Use `frontend-design` + `svelte-sveltekit-expert` for implementation
6. **Run `mcp__svelte__svelte-autofixer`** on every .svelte file before finalizing
7. Use `documentation-writer` to update SITE.md after changes

### Automatic Skill Triggers

Use these skills automatically when you detect these patterns:

| Trigger | Action |
|---------|--------|
| Editing any `.svelte` file | Run `mcp__svelte__svelte-autofixer` before finishing |
| No `SITE.md` exists | Run `/onboarding` skill immediately |
| User shares a URL to copy/remake | Run `/page-remake` skill |
| User mentions "CMS" or "edit content myself" | Run `/sanity-cms` skill |
| After ANY file change in `src/` | Update `SITE.md` using documentation-writer |
| Unsure about Svelte 5 syntax | Use `mcp__svelte__get-documentation` |

### MCP Tools Available

This project has MCP servers configured. Use these tools directly:

**Svelte MCP (`mcp__svelte__*`):**
- `mcp__svelte__list-sections` - List available documentation
- `mcp__svelte__get-documentation` - Fetch specific docs by section name
- `mcp__svelte__svelte-autofixer` - Validate and fix Svelte code
- `mcp__svelte__playground-link` - Generate shareable playground links

**Playwright MCP** (if available):
- Browser automation for screenshots and testing

**Sanity MCP** (if authenticated):
- CMS content management

---

## Human-First Design Principles

Great design feels intentional and distinctive. These guidelines help create sites that stand out and feel memorable.

### The Goal

Sites should feel:

- **Intentional** - Every choice has a reason
- **Distinctive** - Not a copy of common patterns
- **Memorable** - Something visitors remember
- **Human** - Warm and approachable

### Typography Guidance

Common fonts like Inter, Roboto, and system fonts work well but are everywhere. For distinction, explore alternatives:

**Modern & Clean:**

- Space Grotesk + DM Sans
- Outfit + Source Sans 3
- Sora + Nunito

**Elegant & Refined:**

- Playfair Display + Lato
- Cormorant Garamond + Montserrat
- Fraunces + Work Sans

**Warm & Approachable:**

- Poppins + Nunito Sans
- Quicksand + Open Sans
- Comfortaa + Mulish

These aren't rules—they're starting points. The right font depends on the brand.

### Color Guidance

**Think twice about these common defaults:**

- `#3B82F6` (Tailwind blue-500) as primary accent - it's everywhere
- Purple-to-blue gradients on white backgrounds - very common
- Pure black `#000000` on pure white `#FFFFFF` - can feel harsh

**Consider instead:**

- Off-black (`#1C1917`) on off-white (`#FAFAF9`) for softer contrast
- Custom accent colors that reflect the brand's personality
- The 60-30-10 rule: 60% dominant, 30% secondary, 10% accent

### Layout Guidance

**Common patterns to use thoughtfully:**

- 3-column feature grids with generic icons - try alternatives like 2-column, asymmetric, or bento layouts
- Centered everything - vary alignment for visual interest
- Equal spacing throughout - vary spacing for rhythm

**Background patterns that feel dated:**

- Abstract blob SVGs
- Wave section dividers
- Gradient mesh backgrounds

Alternatives: geometric shapes, grain textures, solid colors with intentional variation, or high-quality photography.

### Writing Guidance

**Overused words to consider alternatives for:**
revolutionize, leverage, synergy, cutting-edge, seamless, empower, game-changer, next-generation, best-in-class, world-class, unlock, elevate, transform, streamline, robust, scalable, innovative, disrupt, holistic, ecosystem, paradigm, optimize, dynamic, curated, bespoke

**Instead:** Be specific. Use numbers. Focus on outcomes. Write like a human talking to another human.

---

## CRITICAL: Maintain Documentation

**You MUST keep documentation updated.** This is essential for non-technical users.

### Files to Maintain

1. **`SITE.md`** - The main documentation file. Update EVERY time you make changes:

   ```markdown
   # [Site Name]

   > [One-sentence tagline]

   ## Brand Identity

   - Personality: [from onboarding]
   - Colors: [what we're using]
   - Fonts: [what we're using]

   ## Pages

   - **Homepage** (`/`) - [description of what's on it]
   - **About** (`/about`) - [description]

   ## Components

   - **Navbar** - [what it contains, how to customize]
   - **Footer** - [what it contains]

   ## Recent Changes

   - [Date]: Added hero section with [description]
   - [Date]: Created contact page

   ## How to Customize

   - To change colors: [simple instructions]
   - To add a new page: [simple instructions]
   ```

2. **Create `SITE.md` immediately** if it doesn't exist (via onboarding).

3. **Update `SITE.md` after EVERY change** - no exceptions.

4. **Use simple language** - Say "the main page" not "the root route". Say "the navigation bar at the top" not "the header component".

---

## Project Structure

```
src/
├── routes/              # SvelteKit file-based routing
│   ├── +layout.svelte   # The wrapper around all pages (has fonts, global styles)
│   ├── +page.svelte     # Homepage - EDIT THIS for the main page
│   └── [folders]/+page.svelte  # Other pages (about/, contact/, etc.)
├── lib/                 # Reusable components (Navbar, Footer, etc.)
│   └── components/      # Put components here
├── app.html             # HTML template
└── app.css              # Global styles + Tailwind
static/                  # Images and static files
```

---

## Rules for Building

### DO:

- Run `/onboarding` for new projects without SITE.md
- Check SITE.md before every task for brand context
- Use skills for visual decisions and code patterns
- Edit `src/routes/+page.svelte` for the homepage
- Use Tailwind CSS classes for ALL styling
- Create components in `src/lib/components/`
- Put images in `static/` folder
- Update `SITE.md` after every change
- Explain what you did in simple terms
- Make intentional, distinctive design choices
- Use Svelte 5 runes syntax (`$state`, `$props`, `$derived`, `$effect`)

### DON'T:

- NEVER create `.html` files - this is Svelte/SvelteKit
- NEVER create separate `.css` files - use Tailwind
- NEVER use `<script>` tags without `lang="ts"` - use TypeScript
- NEVER leave the user confused about what changed
- NEVER use technical jargon without explaining it
- NEVER skip updating SITE.md
- NEVER use Svelte 4 syntax (export let, $: reactive) - use Svelte 5 runes

---

## File-Based Routing

Each folder in `src/routes/` becomes a page:

- `src/routes/+page.svelte` → Homepage (yoursite.com)
- `src/routes/about/+page.svelte` → About page (yoursite.com/about)
- `src/routes/contact/+page.svelte` → Contact page (yoursite.com/contact)
- `src/routes/pricing/+page.svelte` → Pricing page (yoursite.com/pricing)

---

## Example: Creating a New Page

If the user asks for an "About" page:

1. Check `SITE.md` for brand personality
2. Use `marketing-site-design` skill to plan sections
3. Use `brand-identity` skill for visual consistency
4. Create `src/routes/about/+page.svelte` using `svelte-sveltekit-expert` patterns
5. Write copy using `copywriting` skill guidelines
6. **Update `SITE.md`** using `documentation-writer` skill
7. Tell the user: "I created an About page. You can see it by going to /about in the preview."

---

## After Every Task

1. Make the requested changes (using your skills, following design principles)
2. Update `SITE.md` with what changed
3. Tell the user what you did in plain English
4. Let them know how to see the changes

---

## Adding CMS (When Requested)

When the user wants to edit content themselves, run the `/sanity-cms` skill. This will:

1. Set up Sanity CMS in the project
2. Create schemas for editable content
3. Connect the frontend to fetch CMS data
4. Give them a friendly editing dashboard

The `.mcp.json` file is already configured for Sanity. User authenticates via OAuth when first using Sanity tools.

---

## Remember

The user is NOT a developer. They're using Ship Studio to build a website without coding knowledge. Your job is to:

1. **Onboard them properly** (if no SITE.md)
2. **Build what they ask for** (using your skills)
3. **Make it feel distinctive and intentional** (not generic)
4. **Keep everything documented** so they understand their site
5. **Explain things simply**
6. **Make them feel confident** about their project

**ALWAYS use your skills. ALWAYS follow design principles. ALWAYS update SITE.md.**
