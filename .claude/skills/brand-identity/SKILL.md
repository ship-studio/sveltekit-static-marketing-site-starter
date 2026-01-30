---
name: brand-identity
description: Guides distinctive brand colors, typography, and visual choices. Contains human-first design principles to ensure sites look intentional and memorable.
user_invocable: true
invocation: /brand
---

# Brand Identity Skill

This skill ensures every site has a distinctive, intentional visual identity. It provides guidance for creating memorable designs.

## The 60-30-10 Color Rule

Every site needs exactly three color roles:

- **60% - Dominant/Background**: The main canvas (usually neutral)
- **30% - Secondary**: Supporting color for sections, cards, accents
- **10% - Accent**: CTAs, highlights, interactive elements (the "pop")

### Implementation

```css
:root {
	/* 60% - Dominant */
	--color-bg: #fafaf9;
	--color-text: #1c1917;

	/* 30% - Secondary */
	--color-secondary: #e7e5e4;
	--color-secondary-text: #44403c;

	/* 10% - Accent */
	--color-accent: #dc2626;
	--color-accent-hover: #b91c1c;
}
```

### Color Selection by Industry

Use these as STARTING POINTS - always customize:

| Industry        | Dominant              | Secondary            | Accent                           |
| --------------- | --------------------- | -------------------- | -------------------------------- |
| Finance/Legal   | Slate, Stone          | Cool gray            | Navy or Forest                   |
| Health/Wellness | Warm white, Cream     | Sage, Soft green     | Terracotta, Coral                |
| Tech/SaaS       | True white, Cool gray | Slate                | Electric blue, Violet            |
| Food/Restaurant | Cream, Warm white     | Terracotta, Olive    | Deep red, Orange                 |
| Creative/Agency | Off-black, Charcoal   | Warm gray            | Unexpected pop (yellow, magenta) |
| Luxury/Fashion  | Pure white, Black     | Gold, Champagne      | Black or Gold                    |
| Education       | Light cream           | Warm gray, Blue-gray | Warm blue, Green                 |

---

## Typography Guidance

### Common Fonts to Use Thoughtfully

These fonts work well but are everywhere. Consider whether you need distinction:

- Inter
- Roboto
- Arial
- Helvetica (for body text)
- Open Sans
- System fonts stack as primary

### Distinctive Font Pairings

Always pair a **display font** (headings) with a **body font**:

**Modern & Clean:**

- [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) + [DM Sans](https://fonts.google.com/specimen/DM+Sans)
- [Outfit](https://fonts.google.com/specimen/Outfit) + [Source Sans 3](https://fonts.google.com/specimen/Source+Sans+3)
- [Sora](https://fonts.google.com/specimen/Sora) + [Nunito](https://fonts.google.com/specimen/Nunito)

**Elegant & Refined:**

- [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) + [Lato](https://fonts.google.com/specimen/Lato)
- [Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond) + [Montserrat](https://fonts.google.com/specimen/Montserrat)
- [Fraunces](https://fonts.google.com/specimen/Fraunces) + [Work Sans](https://fonts.google.com/specimen/Work+Sans)

**Bold & Energetic:**

- [Bebas Neue](https://fonts.google.com/specimen/Bebas+Neue) + [Public Sans](https://fonts.google.com/specimen/Public+Sans)
- [Oswald](https://fonts.google.com/specimen/Oswald) + [Karla](https://fonts.google.com/specimen/Karla)
- [Anton](https://fonts.google.com/specimen/Anton) + [Rubik](https://fonts.google.com/specimen/Rubik)

**Warm & Approachable:**

- [Poppins](https://fonts.google.com/specimen/Poppins) + [Nunito Sans](https://fonts.google.com/specimen/Nunito+Sans)
- [Quicksand](https://fonts.google.com/specimen/Quicksand) + [Open Sans](https://fonts.google.com/specimen/Open+Sans) (acceptable as body only)
- [Comfortaa](https://fonts.google.com/specimen/Comfortaa) + [Mulish](https://fonts.google.com/specimen/Mulish)

**Creative & Artistic:**

- [Righteous](https://fonts.google.com/specimen/Righteous) + [Lexend](https://fonts.google.com/specimen/Lexend)
- [Archivo Black](https://fonts.google.com/specimen/Archivo+Black) + [Work Sans](https://fonts.google.com/specimen/Work+Sans)
- [Josefin Sans](https://fonts.google.com/specimen/Josefin+Sans) + [Source Sans 3](https://fonts.google.com/specimen/Source+Sans+3)

> **Important:** All fonts above have been verified on Google Fonts as of January 2026. Click the links to preview and get embed codes.

### Font Fallback Stacks

Always include fallbacks for reliability:

```css
/* Example with fallbacks */
--font-display: 'Space Grotesk', ui-sans-serif, system-ui, sans-serif;
--font-body: 'DM Sans', ui-sans-serif, system-ui, sans-serif;

/* Serif example */
--font-display: 'Playfair Display', ui-serif, Georgia, serif;
--font-body: 'Lato', ui-sans-serif, system-ui, sans-serif;
```

### Implementation in SvelteKit

```svelte
<!-- src/routes/+layout.svelte -->
<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link
		href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300..700&family=DM+Sans:wght@400;500;600;700&display=swap"
		rel="stylesheet"
	/>
</svelte:head>
```

```css
/* app.css */
:root {
	--font-display: 'Space Grotesk', sans-serif;
	--font-body: 'DM Sans', sans-serif;
}

h1,
h2,
h3,
h4,
h5,
h6 {
	font-family: var(--font-display);
}

body {
	font-family: var(--font-body);
}
```

---

## Human-First Design Principles

### Colors - Think Twice About

| Common Default                | Why Consider Alternatives            | Alternative Ideas                                              |
| ----------------------------- | ------------------------------------ | -------------------------------------------------------------- |
| `#3B82F6` (Tailwind blue-500) | It's the default, so it's everywhere | Pick a unique blue: `#2563EB`, `#1D4ED8`, or a non-blue accent |
| Purple-to-blue gradient       | Very common pattern                  | Single color, or unexpected gradient (orange→pink, green→teal) |
| Teal + Coral combo            | Overused "modern" palette            | Pick ONE and find a neutral complement                         |
| Rainbow gradients             | Can feel unintentional               | Two-color max, subtle angle                                    |
| Pure `#000000` on `#FFFFFF`   | Harsh contrast                       | Off-black (`#1C1917`) on off-white (`#FAFAF9`)                 |

### Layouts - Consider Alternatives

| Common Pattern                       | Why Try Alternatives            | Alternative Ideas                                      |
| ------------------------------------ | ------------------------------- | ------------------------------------------------------ |
| 3-column feature grid with icons     | Very common, can feel templated | 2-column, asymmetric, or bento grid                    |
| Centered everything                  | Predictable                     | Left-align body, vary section alignment                |
| Equal spacing throughout             | Can feel mechanical             | Vary spacing: tight headers, generous between sections |
| Generic icon set (Heroicons default) | Recognizable as defaults        | Phosphor Icons, Lucide with custom stroke, or no icons |

### Backgrounds - Patterns That Feel Dated

| Pattern                   | Why It Feels Dated       | Alternatives                                        |
| ------------------------- | ------------------------ | --------------------------------------------------- |
| Abstract blob SVGs        | Was trendy, now overused | Geometric shapes, grain texture, or solid color     |
| Wave dividers             | 2020 template aesthetic  | Hard edges, diagonal slices, or no dividers         |
| Gradient mesh backgrounds | Overplayed               | Subtle radial gradient, solid color, or photography |
| Grid of dots              | Very common              | Lines, noise texture, or nothing                    |

### Images - Generic vs Intentional

| Generic Choice                   | Why Consider Alternatives | Better Options                                          |
| -------------------------------- | ------------------------- | ------------------------------------------------------- |
| Handshake stock photos           | Meaningless corporate     | Real team photos or none                                |
| Diverse group pointing at laptop | Overused cliche           | Action shots or illustrations                           |
| Abstract 3D shapes               | Very common default       | Real photos, custom illustration, or typography-focused |
| Floating UI mockups              | Template aesthetic        | Screenshots in context or no mockups                    |

---

## Applying Brand to Site

When building, CHECK every component against:

1. **Does it use common defaults?** Consider if distinction is needed
2. **Does it follow 60-30-10?** Check color distribution
3. **Are fonts properly loaded?** (Google Fonts, CSS variables)
4. **Does it feel intentional?** Every choice should have a reason

### Quick Improvements for Generic-Looking Sites

| Issue                 | Fix                                                |
| --------------------- | -------------------------------------------------- |
| Looks too "template"  | Add asymmetry, vary section layouts                |
| Colors feel generic   | Commit to ONE bold accent, desaturate the rest     |
| Typography feels flat | Increase heading size contrast, add letter-spacing |
| Too much whitespace   | Add subtle background texture or tint              |
| Too busy              | Remove one element from every section              |
| Feels corporate       | Add one unexpected color or playful element        |

---

## Checklist Before Shipping

- [ ] Typography choices are intentional (not just defaults)
- [ ] Colors feel distinctive (not just Tailwind defaults)
- [ ] Layout has visual interest (not all centered/equal)
- [ ] 60-30-10 color rule followed
- [ ] Fonts loaded via Google Fonts with fallback stacks
- [ ] Font availability verified at fonts.google.com
- [ ] At least ONE distinctive design choice per page
- [ ] Design feels intentional and human
- [ ] CSS variables defined for colors and fonts (maintainability)
