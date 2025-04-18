<script lang="ts">
	import Header from '$lib/components/Header.svelte';
	import Footer from '$lib/components/Footer.svelte';
	import AccessibilityButton from '$lib/components/AccessibilityButton.svelte';
	import '../app.css';
	export let data;
</script>

<svelte:head>
	<link rel="icon" href="/favicon.ico" />
	<meta name="viewport" content="width=device-width, initial-scale=1" />
	<meta name="theme-color" content="#171123" />
	<meta
		name="description"
		content="Portfolio of Travis Peterson, Creative Technologist and Strategist."
	/>
	<title>Clothesline Studio | Travis Peterson</title>
</svelte:head>

<div
	class="flex min-h-screen flex-col bg-[var(--color-bg)] text-[var(--color-text)] transition-colors duration-300"
>
	<Header />
	<main role="main" class="flex-grow px-4 py-8 sm:px-6 lg:px-8">
		<div class="mx-auto max-w-7xl">
			<slot />
		</div>
		<AccessibilityButton />
	</main>
	<Footer />
</div>
