---
name: frontend-design
description: Create distinctive, production-grade frontend interfaces with high design quality. Use this skill when the user asks to build web components, pages, or applications. Generates creative, polished code that feels intentional and memorable.
---

This skill guides creation of distinctive, production-grade frontend interfaces that feel intentional and human-crafted. Implement real working code with exceptional attention to aesthetic details and creative choices.

The user provides frontend requirements: a component, page, application, or interface to build. They may include context about the purpose, audience, or technical constraints.

## Design Thinking

Before coding, understand the context and commit to a BOLD aesthetic direction:

- **Purpose**: What problem does this interface solve? Who uses it?
- **Tone**: Pick an extreme: brutally minimal, maximalist chaos, retro-futuristic, organic/natural, luxury/refined, playful/toy-like, editorial/magazine, brutalist/raw, art deco/geometric, soft/pastel, industrial/utilitarian, etc. There are so many flavors to choose from. Use these for inspiration but design one that is true to the aesthetic direction.
- **Constraints**: Technical requirements (framework, performance, accessibility).
- **Differentiation**: What makes this UNFORGETTABLE? What's the one thing someone will remember?

**CRITICAL**: Choose a clear conceptual direction and execute it with precision. Bold maximalism and refined minimalism both work - the key is intentionality, not intensity.

**Note:** This project uses **Tailwind CSS v4**, which has different syntax than v3:

- Gradients: `bg-linear-to-br` (not `bg-gradient-to-br`)
- Arbitrary values: `aspect-4/3` works directly (no brackets needed)

Then implement working code (Svelte components with TypeScript) that is:

- Production-grade and functional
- Visually striking and memorable
- Cohesive with a clear aesthetic point-of-view
- Meticulously refined in every detail
- Properly typed with TypeScript interfaces

## Frontend Aesthetics Guidelines

Focus on:

- **Typography**: Choose fonts that are beautiful, unique, and interesting. Common fonts like Arial and Inter work but are everywhere; opt instead for distinctive choices that elevate the frontend's aesthetics. Pair a distinctive display font with a refined body font.
- **Color & Theme**: Commit to a cohesive aesthetic. Use CSS variables for consistency. Dominant colors with sharp accents outperform timid, evenly-distributed palettes.
- **Motion**: Use CSS transitions and animations for effects and micro-interactions. Focus on high-impact moments: one well-orchestrated page load with staggered reveals creates more delight than scattered micro-interactions. Use scroll-triggering and hover states that surprise.
- **Spatial Composition**: Unexpected layouts. Asymmetry. Overlap. Diagonal flow. Grid-breaking elements. Generous negative space OR controlled density.
- **Backgrounds & Visual Details**: Create atmosphere and depth rather than defaulting to solid colors. Add contextual effects and textures that match the overall aesthetic. Apply creative forms like gradient meshes, noise textures, geometric patterns, layered transparencies, dramatic shadows, decorative borders, custom cursors, and grain overlays.

Think twice about generic aesthetics like overused font families (Inter, Roboto, Arial, system fonts), common color schemes (particularly purple gradients on white backgrounds), predictable layouts and component patterns, and cookie-cutter designs that lack context-specific character.

Interpret creatively and make unexpected choices that feel genuinely designed for the context. No design should be the same. Vary between light and dark themes, different fonts, different aesthetics. The goal is to avoid converging on common choices across designs.

**IMPORTANT**: Match implementation complexity to the aesthetic vision. Maximalist designs need elaborate code with extensive animations and effects. Minimalist or refined designs need restraint, precision, and careful attention to spacing, typography, and subtle details. Elegance comes from executing the vision well.

Remember: Claude is capable of extraordinary creative work. Don't hold back—show what can truly be created when thinking outside the box and committing fully to a distinctive vision.

---

## Example Patterns

### Distinctive Hero Section

```svelte
<script lang="ts">
	interface Props {
		headline: string;
		subheadline: string;
	}

	let { headline, subheadline }: Props = $props();
</script>

<section class="relative min-h-[90vh] flex items-center overflow-hidden">
	<!-- Subtle grain texture overlay -->
	<div
		class="absolute inset-0 opacity-[0.03] pointer-events-none"
		style="background-image: url('data:image/svg+xml,...')"
	></div>

	<!-- Asymmetric layout -->
	<div class="max-w-7xl mx-auto px-6 grid lg:grid-cols-[1.2fr,1fr] gap-16 items-center">
		<div class="space-y-8">
			<h1
				class="text-5xl md:text-7xl font-display font-bold tracking-tight text-stone-900 leading-[1.1]"
			>
				{headline}
			</h1>
			<p class="text-xl text-stone-600 max-w-lg leading-relaxed">
				{subheadline}
			</p>
			<div class="flex gap-4">
				<button
					class="px-8 py-4 bg-stone-900 text-white rounded-full hover:bg-stone-800 transition-colors"
				>
					Get Started
				</button>
			</div>
		</div>

		<!-- Visual element with intentional offset -->
		<div class="relative lg:-mr-24">
			<div
				class="aspect-4/3 rounded-3xl bg-linear-to-br from-amber-100 to-orange-50 shadow-2xl"
			></div>
		</div>
	</div>
</section>
```

### Card with Personality

```svelte
<script lang="ts">
	interface Props {
		title: string;
		description: string;
		accent?: 'rose' | 'amber' | 'emerald';
	}

	let { title, description, accent = 'rose' }: Props = $props();

	const accentClasses: Record<string, string> = {
		rose: 'group-hover:bg-rose-500',
		amber: 'group-hover:bg-amber-500',
		emerald: 'group-hover:bg-emerald-500'
	};
</script>

<article
	class="group relative p-8 bg-white rounded-2xl border border-stone-200 hover:border-stone-300 transition-all duration-300 hover:shadow-lg hover:-translate-y-1"
>
	<!-- Accent line that animates on hover -->
	<div class="absolute top-0 left-8 right-8 h-1 bg-stone-200 rounded-full overflow-hidden">
		<div
			class="h-full w-0 group-hover:w-full {accentClasses[accent]} transition-all duration-500"
		></div>
	</div>

	<h3 class="mt-4 text-xl font-semibold text-stone-900">{title}</h3>
	<p class="mt-3 text-stone-600 leading-relaxed">{description}</p>
</article>
```

### Animated Stats Section

```svelte
<script lang="ts">
	const stats = [
		{ value: '10K+', label: 'Happy customers' },
		{ value: '99.9%', label: 'Uptime' },
		{ value: '24/7', label: 'Support' }
	];
</script>

<section class="py-24 bg-stone-900 text-white">
	<div class="max-w-5xl mx-auto px-6">
		<div class="grid md:grid-cols-3 gap-12 text-center">
			{#each stats as stat, i}
				<div class="space-y-2" style="animation: fadeUp 0.6s ease-out {i * 0.1}s both">
					<div class="text-5xl font-bold tracking-tight">{stat.value}</div>
					<div class="text-stone-400">{stat.label}</div>
				</div>
			{/each}
		</div>
	</div>
</section>

<style>
	@keyframes fadeUp {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}
</style>
```

---

## Integration with Other Skills

| Need                    | Skill to Reference        |
| ----------------------- | ------------------------- |
| Color palette decisions | `brand-identity`          |
| Section architecture    | `marketing-site-design`   |
| Copy and headlines      | `copywriting`             |
| Animations and motion   | `animations`              |
| Code patterns           | `svelte-sveltekit-expert` |
