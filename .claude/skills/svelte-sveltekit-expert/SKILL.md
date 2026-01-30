---
name: svelte-sveltekit-expert
description: Expert guidance for SvelteKit 2 with Svelte 5 development. Use this skill when creating components, pages, layouts, or any Svelte/SvelteKit code. Ensures proper patterns for file-based routing, Svelte 5 runes, data loading, and Tailwind CSS styling.
---

# Svelte & SvelteKit Expert

Expert guidance for SvelteKit 2 with Svelte 5 (runes). This project uses static site generation.

## File-Based Routing

```
src/routes/
├── +page.svelte           → yoursite.com
├── about/+page.svelte     → yoursite.com/about
├── blog/[slug]/+page.svelte → yoursite.com/blog/any-post
├── +layout.svelte         → Wraps all pages (navigation, footer)
└── +error.svelte          → Error page
```

## Svelte 5 Runes

**ALWAYS use Svelte 5 runes syntax**, never the old Svelte 4 syntax:

```svelte
<script lang="ts">
  // Props (replaces "export let")
  let { name, count = 0 } = $props();

  // State (replaces "let x = 0")
  let counter = $state(0);

  // Derived values (replaces "$: doubled = count * 2")
  let doubled = $derived(counter * 2);

  // Effects (replaces "$: { ... }")
  $effect(() => {
    console.log('Counter changed:', counter);
  });
</script>
```

## Component Patterns

**Page component:**
```svelte
<script lang="ts">
  // No props needed for pages typically
</script>

<main class="min-h-screen p-8">
  <h1 class="text-4xl font-bold">About Us</h1>
  <p class="mt-4 text-gray-600">Our story...</p>
</main>
```

**Reusable component with props:**
```svelte
<!-- src/lib/components/Button.svelte -->
<script lang="ts">
  interface Props {
    variant?: 'primary' | 'secondary';
    onclick?: () => void;
    children: import('svelte').Snippet;
  }

  let { variant = 'primary', onclick, children }: Props = $props();

  let styles = $derived(
    variant === 'primary' ? 'bg-blue-600 text-white' : 'bg-gray-200 text-gray-800'
  );
</script>

<button class="px-4 py-2 rounded {styles}" {onclick}>
  {@render children()}
</button>
```

## Using Children (Snippets)

Svelte 5 uses snippets instead of slots:

```svelte
<script lang="ts">
  let { children } = $props();
</script>

<div class="wrapper">
  {@render children()}
</div>
```

## Layout Pattern

```svelte
<!-- src/routes/+layout.svelte -->
<script lang="ts">
  import '../app.css';

  let { children } = $props();
</script>

<nav class="p-4 bg-gray-100">
  <a href="/">Home</a>
  <a href="/about" class="ml-4">About</a>
</nav>

{@render children()}

<footer class="p-4 bg-gray-100 mt-8">
  &copy; {new Date().getFullYear()} My Site
</footer>
```

## Tailwind CSS

Use Tailwind classes for all styling. Never create separate CSS files.

**Common patterns:**
```svelte
<!-- Spacing: p-4, m-2, px-6, py-3, mt-8, mb-4 -->
<!-- Text: text-xl, font-bold, text-gray-600, text-center -->
<!-- Layout: flex, grid, items-center, justify-between -->
<!-- Sizing: w-full, h-screen, max-w-4xl, min-h-screen -->
<!-- Colors: bg-blue-600, text-white, border-gray-300 -->
<!-- Responsive: md:flex-row, lg:text-xl, sm:p-4 -->
```

## Images

```svelte
<!-- From static folder -->
<img src="/logo.png" alt="Company Logo" class="w-48 h-auto" />

<!-- Or use enhanced:img for optimization (requires setup) -->
<enhanced:img src="/logo.png" alt="Company Logo" />
```

## Links

```svelte
<!-- Standard anchor tags work in SvelteKit -->
<a href="/about" class="text-blue-600 hover:underline">About Us</a>

<!-- For programmatic navigation -->
<script lang="ts">
  import { goto } from '$app/navigation';

  function navigate() {
    goto('/about');
  }
</script>
```

## Event Handlers

Use lowercase event names:

```svelte
<button onclick={() => count++}>Click me</button>
<input oninput={(e) => name = e.currentTarget.value} />
<form onsubmit={handleSubmit}>...</form>
```

## Conditional Rendering

```svelte
{#if condition}
  <p>Shown when true</p>
{:else if otherCondition}
  <p>Alternative</p>
{:else}
  <p>Fallback</p>
{/if}
```

## Lists

```svelte
{#each items as item, index (item.id)}
  <div>{index}: {item.name}</div>
{/each}
```

## Common Mistakes to Avoid

1. **Don't use Svelte 4 syntax** - No `export let`, no `$:` reactivity
2. **Don't create .html files** - This is Svelte, use .svelte
3. **Don't use `<script>` without `lang="ts"`** - Always use TypeScript
4. **Don't create .css files** - Use Tailwind classes
5. **Don't forget to use runes** - `$state`, `$derived`, `$effect`, `$props`
6. **Don't use `on:click`** - Use `onclick` (Svelte 5 syntax)
7. **Don't use `<slot>`** - Use snippets with `{@render children()}`

## Svelte 4 vs Svelte 5 Quick Reference

| Svelte 4 | Svelte 5 |
|----------|----------|
| `export let prop` | `let { prop } = $props()` |
| `let count = 0` | `let count = $state(0)` |
| `$: doubled = count * 2` | `let doubled = $derived(count * 2)` |
| `$: { console.log(x) }` | `$effect(() => { console.log(x) })` |
| `on:click={handler}` | `onclick={handler}` |
| `<slot />` | `{@render children()}` |
