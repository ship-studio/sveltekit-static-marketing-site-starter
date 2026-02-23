<script lang="ts">
	const capabilities = [
		'Landing pages',
		'Web apps',
		'Portfolios',
		'Company websites',
		'Dashboards',
		'SaaS products',
		'Event sites',
		'Personal sites'
	];
</script>

<div class="min-h-screen bg-background">
	<main class="mx-auto max-w-3xl px-6 py-16 sm:py-24">
		<!-- Welcome Hero -->
		<header class="mb-16">
			<p class="mb-3 text-sm font-medium uppercase tracking-wider text-muted">Welcome to</p>
			<h1 class="mb-4 font-display text-4xl font-bold tracking-tight text-foreground sm:text-5xl">
				Ship Studio
			</h1>
			<p class="text-lg text-muted">
				How professionals build with AI. Just describe what you want.
			</p>
		</header>

		<!-- Getting Started -->
		<section class="mb-16">
			<h2 class="mb-6 font-display text-2xl font-semibold text-foreground">Getting Started</h2>
			<div class="space-y-6">
				<div class="flex gap-4">
					<div
						class="flex h-8 w-8 shrink-0 items-center justify-center rounded-full bg-foreground text-sm font-semibold text-background"
					>
						1
					</div>
					<div>
						<h3 class="font-semibold text-foreground">Start a conversation</h3>
						<p class="text-muted">
							Just type what you want to build. A landing page, a web app, a portfolio — anything.
						</p>
					</div>
				</div>
				<div class="flex gap-4">
					<div
						class="flex h-8 w-8 shrink-0 items-center justify-center rounded-full bg-foreground text-sm font-semibold text-background"
					>
						2
					</div>
					<div>
						<h3 class="font-semibold text-foreground">AI builds it</h3>
						<p class="text-muted">
							Your AI handles the code. Watch your project come together in real-time.
						</p>
					</div>
				</div>
				<div class="flex gap-4">
					<div
						class="flex h-8 w-8 shrink-0 items-center justify-center rounded-full bg-foreground text-sm font-semibold text-background"
					>
						3
					</div>
					<div>
						<h3 class="font-semibold text-foreground">Refine together</h3>
						<p class="text-muted">
							Ask for changes, add pages, tweak colors. Keep iterating until it's perfect.
						</p>
					</div>
				</div>
			</div>
		</section>

		<!-- Available Commands -->
		<section class="mb-16">
			<h2 class="mb-6 font-display text-2xl font-semibold text-foreground">Available Commands</h2>
			<div class="space-y-4">
				<div class="rounded-lg border border-foreground/10 p-4">
					<code class="text-sm font-semibold text-accent">/onboarding</code>
					<p class="mt-1 text-muted">
						Set up a new project. I'll ask about your business and create a personalized build plan.
					</p>
				</div>
				<div class="rounded-lg border border-foreground/10 p-4">
					<code class="text-sm font-semibold text-accent">/page-remake</code>
					<p class="mt-1 text-muted">
						Rebuild from an example. Share a URL you like, and I'll create something similar but
						better.
					</p>
				</div>
				<div class="rounded-lg border border-foreground/10 p-4">
					<code class="text-sm font-semibold text-accent">/sanity-cms</code>
					<p class="mt-1 text-muted">
						Add editable content. When you want to update text yourself without touching code.
					</p>
				</div>
			</div>
		</section>

		<!-- What You Can Build -->
		<section class="mb-16">
			<h2 class="mb-6 font-display text-2xl font-semibold text-foreground">What You Can Build</h2>
			<div class="flex flex-wrap gap-3">
				{#each capabilities as item}
					<span class="rounded-full border border-foreground/10 px-4 py-2 text-sm text-foreground">
						{item}
					</span>
				{/each}
			</div>
			<p class="mt-4 text-muted">All built with AI, at professional quality.</p>
		</section>

		<!-- Quick Start -->
		<section class="rounded-lg bg-foreground p-6 text-background">
			<h2 class="mb-2 font-display text-xl font-semibold">Ready to start?</h2>
			<p class="opacity-80">Just describe what you want to build. Your AI takes it from there.</p>
		</section>
	</main>
</div>
