---
name: page-remake
description: Remake and improve existing web pages from URL examples. Use when user provides a URL and asks to "remake", "rebuild", "recreate", or "use as inspiration" for their site. Screenshots the original, analyzes branding, and rebuilds section-by-section.
user_invocable: true
---

# Page Remake Skill

This skill transforms existing web pages into your own version. It captures the essence of the original and rebuilds it in your codebase.

## When to Trigger

**Automatically run this skill when user says:**
- "Remake this page: [URL]"
- "Start from this example: [URL]"
- "I want my site to look like this: [URL]"
- "Rebuild this: [URL]"
- "Use this as inspiration: [URL]"
- "Make my site like [URL]"
- "Copy the style of [URL]"
- "Recreate this: [URL]"

**Also trigger when:**
- User shares a URL and asks you to "replicate", "mirror", or "build something similar"
- User says "I like this website" followed by a URL
- User provides a screenshot and says "make it like this"

---

## Phase 1: Screenshot the Original

### Using Playwright MCP

Navigate to the URL and capture a full-page screenshot:

```
1. Use browser_navigate to go to the URL
2. Wait for the page to fully load (give it a moment for images/animations)
3. Use browser_screenshot to capture the full page
4. Save screenshot to static/references/ for ongoing comparison
```

### Screenshot Storage

Create the references directory if it doesn't exist:
```
static/
└── references/
    └── original-[sitename]-[date].png
```

**Tell the user:** "I'm taking a screenshot of [URL] so I can study its design. This will be my reference as I rebuild each section."

---

## Phase 1.5: Choose Your Approach

After capturing the screenshot, ask the user which approach they prefer:

> "I've captured the original. How should I approach this remake?
>
> **Option 1: Exact Remake**
> Recreate each section as closely as possible—same structure, layout, content patterns.
> Best if: You love the original and just need it in your codebase.
>
> **Option 2: Same Brand, Fresh Build**
> Keep the fonts, colors, and brand feel. May reorganize or improve layouts.
> Best if: You want the brand identity but are open to improvements.
>
> **Option 3: Inspired Remake** (Recommended)
> Capture the essence but apply thoughtful design choices—distinctive fonts, optimized layouts, better copy.
> Best if: You want something that feels similar but with intentional improvements."

Wait for the user's choice before proceeding.

---

## Phase 2: Analyze & Create Brand Document

After capturing the screenshot, perform a detailed visual analysis.

### What to Analyze

Study the screenshot carefully and document:

1. **Color Palette**
   - Primary color (dominant brand color)
   - Secondary colors (supporting tones)
   - Accent color (CTAs, highlights)
   - Background colors (sections, cards)
   - Text colors (headings vs body)

2. **Typography**
   - Heading font style (serif, sans-serif, display)
   - Body text style
   - Font weights used
   - Letter spacing patterns
   - Text sizes hierarchy

3. **Layout Patterns**
   - Hero style (full-width, split, minimal)
   - Section structures (how content is organized)
   - Grid patterns (columns, asymmetry)
   - Spacing rhythm (tight, generous, varied)
   - Visual flow (Z-pattern, F-pattern, scrolling)

4. **Visual Elements**
   - Image treatment (photography style, filters)
   - Icons (style, consistency, usage)
   - Decorative elements (shapes, lines, backgrounds)
   - Buttons/CTAs (shape, style, hover states)

5. **Brand Messaging**
   - Tone of voice (formal/casual, serious/playful)
   - Key value propositions
   - Target audience signals
   - Emotional appeal

6. **Section Inventory**
   - List each section from top to bottom
   - Note the purpose of each section
   - Document layout/structure of each

### Create BRAND-ANALYSIS.md

Save this to the project root with a detailed analysis (see full template in the skill).

---

## Phase 3: Handle SITE.md

Before building, check for existing SITE.md and ask the user how to proceed.

### If SITE.md EXISTS

Ask the user:

> "I found an existing SITE.md with your project information. How would you like to proceed?
>
> **Option A: Merge** - I'll blend insights from [URL] with your existing brand identity
>
> **Option B: Fresh Start** - I'll create a new SITE.md based entirely on [URL]'s brand analysis
>
> Which do you prefer?"

### If SITE.md DOES NOT EXIST

Create SITE.md using the brand analysis as the visual foundation, but ask key business questions first.

---

## Phase 4: Section-by-Section Rebuild

Build each section one at a time, referencing the original screenshot.

### Approach-Specific Guidelines

#### For Exact Remake
- Replicate layouts faithfully
- Match colors as closely as possible
- Find closest Google Font matches for typography
- Preserve content structure and hierarchy

#### For Same Brand, Fresh Build
- Use original fonts/colors exactly or find closest matches
- Preserve the overall brand feel
- May suggest layout improvements if beneficial

#### For Inspired Remake (Recommended)
- Full creative freedom with design choices
- Apply human-first design principles
- Choose distinctive fonts that match the brand feel
- Optimize layouts for clarity and impact

### For EACH Section:

1. **Reference the Original** - Look at layout, content, visual treatment
2. **Apply Selected Approach Rules** - Match faithfully or improve
3. **Write Copy** - Use copywriting skill guidelines
4. **Implement the Section** - Use svelte-sveltekit-expert patterns

### Section Build Order

1. **Hero** - Sets the tone for everything
2. **Social Proof Bar** - Early credibility (if original has one)
3. **Main Content Sections** - Features, benefits, how it works
4. **Testimonials** - Social proof
5. **Final CTA** - Conversion section
6. **Navbar** - Navigation (do this alongside hero)
7. **Footer** - Links and secondary info

---

## Phase 5: Quality Verification

After rebuilding all sections, compare with the original and verify the approach-specific requirements were met.

### Checklist

**For All Approaches:**
- [ ] Brand feel is captured
- [ ] Colors work well together
- [ ] Typography hierarchy is clear
- [ ] Copy is specific and human-sounding
- [ ] Mobile responsive
- [ ] Accessible (proper headings, alt text, contrast)

---

## Integration with Other Skills

This skill orchestrates multiple other skills:

| Skill | When to Use |
|-------|-------------|
| **brand-identity** | Check all color/font choices |
| **copywriting** | Write all text content (headlines, body, CTAs) |
| **marketing-site-design** | Section architecture and conversion patterns |
| **frontend-design** | Visual implementation and creative direction |
| **svelte-sveltekit-expert** | Code implementation patterns |
| **documentation-writer** | Update SITE.md after completion |

---

## Files Created

| File | Location | Purpose |
|------|----------|---------|
| `BRAND-ANALYSIS.md` | Project root | Detailed analysis of original |
| Original screenshot | `static/references/` | Visual reference during build |
| `SITE.md` | Project root | Updated/created project documentation |
| Page components | `src/routes/` and `src/lib/` | The rebuilt page |
