<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="preconnect" href="https://fonts.googleapis.com" />
	<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin="anonymous" />
	<link
		href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,100..1000;1,9..40,100..1000&family=Space+Grotesk:wght@300..700&display=swap"
		rel="stylesheet"
	/>
	<title>Ship Studio</title>
	<meta name="description" content="Build marketing sites with Claude Code. No coding required." />
</svelte:head>

<div class="font-[family-name:var(--font-body)] antialiased">
	{@render children()}
</div>
