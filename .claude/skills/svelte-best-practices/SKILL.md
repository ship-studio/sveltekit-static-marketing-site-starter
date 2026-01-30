---
name: svelte-best-practices
description: Performance optimization and best practices for Svelte 5 applications. Use this skill when optimizing components, managing state, or ensuring the site performs well.
---

# Svelte Best Practices

Performance and optimization guidelines for Svelte 5 applications.

## State Management

### Use Fine-Grained Reactivity

```svelte
<script lang="ts">
  // Good: Fine-grained state
  let user = $state({
    name: 'John',
    email: 'john@example.com'
  });

  // Accessing properties is reactive
  // Only components using user.name will update when name changes
</script>

<p>{user.name}</p>
```

### Avoid Unnecessary State

```svelte
<script lang="ts">
  let { items } = $props();

  // Good: Derived from props, no extra state needed
  let total = $derived(items.reduce((sum, item) => sum + item.price, 0));

  // Bad: Duplicating state
  // let total = $state(0);
  // $effect(() => { total = items.reduce(...) });
</script>
```

## Component Optimization

### Keep Components Small

Split large components into smaller, focused ones:

```svelte
<!-- Good: Small, focused component -->
<!-- src/lib/components/ProductCard.svelte -->
<script lang="ts">
  let { product } = $props();
</script>

<article class="p-4 border rounded">
  <h3>{product.name}</h3>
  <p>{product.price}</p>
</article>
```

### Lazy Load Heavy Components

```svelte
<script lang="ts">
  import { onMount } from 'svelte';

  let HeavyComponent: any = $state(null);

  onMount(async () => {
    const module = await import('$lib/components/HeavyComponent.svelte');
    HeavyComponent = module.default;
  });
</script>

{#if HeavyComponent}
  <svelte:component this={HeavyComponent} />
{:else}
  <p>Loading...</p>
{/if}
```

## Image Optimization

### Use Proper Image Sizing

```svelte
<!-- Specify dimensions to prevent layout shift -->
<img
  src="/hero.jpg"
  alt="Hero image"
  width="1200"
  height="600"
  class="w-full h-auto"
  loading="lazy"
/>
```

### Lazy Load Below-the-Fold Images

```svelte
<img src="/image.jpg" alt="Description" loading="lazy" />
```

## CSS Best Practices

### Use Tailwind Efficiently

```svelte
<!-- Good: Utility classes -->
<div class="flex items-center gap-4 p-4 bg-white rounded-lg shadow">
  ...
</div>

<!-- Avoid: Inline styles -->
<div style="display: flex; align-items: center;">
  ...
</div>
```

### Extract Repeated Patterns

If you use the same combination often, create a component:

```svelte
<!-- src/lib/components/Card.svelte -->
<script lang="ts">
  let { children } = $props();
</script>

<div class="p-6 bg-white rounded-lg shadow-md">
  {@render children()}
</div>
```

## Event Handling

### Debounce Expensive Operations

```svelte
<script lang="ts">
  let searchQuery = $state('');
  let debouncedQuery = $state('');

  $effect(() => {
    const timeout = setTimeout(() => {
      debouncedQuery = searchQuery;
    }, 300);

    return () => clearTimeout(timeout);
  });
</script>

<input
  type="text"
  value={searchQuery}
  oninput={(e) => searchQuery = e.currentTarget.value}
/>
```

## Accessibility

### Always Include Alt Text

```svelte
<img src="/photo.jpg" alt="A person typing on a laptop" />
```

### Use Semantic HTML

```svelte
<!-- Good -->
<nav>...</nav>
<main>...</main>
<article>...</article>
<section>...</section>
<footer>...</footer>

<!-- Bad -->
<div class="nav">...</div>
<div class="main">...</div>
```

### Ensure Keyboard Navigation

```svelte
<button onclick={handleClick}>Click me</button>

<!-- Not a button? Add keyboard support -->
<div
  role="button"
  tabindex="0"
  onclick={handleClick}
  onkeydown={(e) => e.key === 'Enter' && handleClick()}
>
  Custom button
</div>
```

## Error Handling

### Handle Loading States

```svelte
<script lang="ts">
  let loading = $state(true);
  let error = $state<string | null>(null);
  let data = $state<any>(null);

  async function fetchData() {
    try {
      loading = true;
      error = null;
      const response = await fetch('/api/data');
      data = await response.json();
    } catch (e) {
      error = 'Failed to load data';
    } finally {
      loading = false;
    }
  }
</script>

{#if loading}
  <p>Loading...</p>
{:else if error}
  <p class="text-red-600">{error}</p>
{:else}
  <div>{data}</div>
{/if}
```

## Performance Checklist

Before shipping, verify:

- [ ] Images have width/height attributes
- [ ] Below-fold images use `loading="lazy"`
- [ ] No unnecessary state (use `$derived` when possible)
- [ ] Components are reasonably sized
- [ ] Expensive operations are debounced
- [ ] All images have alt text
- [ ] Semantic HTML is used
- [ ] Interactive elements are keyboard accessible
