<script lang="ts">
	import { onMount } from 'svelte';
	import type { ComponentType } from 'svelte';

	export let data: {
		content: ComponentType;
		metadata: { title?: string };
	};

	let toc: { id: string; text: string; level: number }[] = [];

	onMount(() => {
		const headings = Array.from(
			document.querySelectorAll('article h2, article h3')
		) as HTMLHeadingElement[];

		toc = headings.map((heading) => ({
			id: heading.id || heading.innerText.toLowerCase().replace(/\s+/g, '-'),
			text: heading.innerText,
			level: heading.tagName === 'H2' ? 2 : 3
		}));

		headings.forEach((heading, index) => {
			if (!heading.id) {
				heading.id = toc[index].id;
			}
		});
	});
</script>

<!-- Breadcrumb navigation -->
<nav class="mb-6 text-sm text-gray-500">
	<a href="/" class="hover:underline">Home</a>
	<span class="mx-2">/</span>
	<a href="/docs" class="hover:underline">Docs</a>
	<span class="mx-2">/</span>
	<span class="font-semibold text-gray-700">{data.metadata.title ?? 'Untitled'}</span>
</nav>

<!-- Layout: main content first, TOC floated to right on large screens -->
<div class="flex flex-col-reverse gap-10 lg:flex-row lg:items-start">
	<!-- Main article content -->
	<article
		class="prose dark:prose-invert
                prose-headings:text-[var(--color-accent)]
                prose-p:text-[var(--color-text)]
                prose-a:text-[var(--color-accent)]
                prose-code:bg-[rgba(0,0,0,0.05)]
                dark:prose-code:bg-[rgba(255,255,255,0.1)]
                mx-auto max-w-4xl p-6"
	>
		{#if data.content}
			<svelte:component this={data.content} />
		{:else}
			<p>Loading...</p>
		{/if}
	</article>

	<!-- Table of Contents -->
	{#if toc.length > 1}
		<aside class="sticky top-20 hidden w-64 flex-shrink-0 self-start lg:block">
			<div class="space-y-2 text-sm text-gray-400">
				<h2 class="mb-4 font-bold text-gray-300">On this page</h2>
				{#each toc as item}
					<a
						href={'#' + item.id}
						class={`block ${item.level === 3 ? 'ml-4' : 'ml-0'} transition hover:text-[var(--color-accent)]`}
					>
						{item.text}
					</a>
				{/each}
			</div>
		</aside>
	{/if}
</div>
