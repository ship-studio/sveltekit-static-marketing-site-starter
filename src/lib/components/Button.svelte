<script lang="ts">
	import type { Snippet } from 'svelte';
	import type { HTMLButtonAttributes } from 'svelte/elements';

	interface Props extends HTMLButtonAttributes {
		variant?: 'primary' | 'secondary' | 'outline';
		size?: 'sm' | 'md' | 'lg';
		children: Snippet;
	}

	let {
		variant = 'primary',
		size = 'md',
		children,
		class: className = '',
		...rest
	}: Props = $props();

	const baseStyles =
		'inline-flex items-center justify-center font-medium transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-accent disabled:pointer-events-none disabled:opacity-50';

	const variants = {
		primary: 'bg-accent text-accent-foreground hover:bg-accent/90',
		secondary: 'bg-foreground text-background hover:bg-foreground/90',
		outline: 'border border-foreground/20 bg-transparent hover:bg-foreground/5'
	};

	const sizes = {
		sm: 'h-8 px-3 text-sm rounded-md',
		md: 'h-10 px-4 text-sm rounded-lg',
		lg: 'h-12 px-6 text-base rounded-lg'
	};
</script>

<button class="{baseStyles} {variants[variant]} {sizes[size]} {className}" {...rest}>
	{@render children()}
</button>
