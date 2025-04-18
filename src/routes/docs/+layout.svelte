<script lang="ts">
	export let data: { docs: { slug: string; title: string }[] };
</script>

<div class="flex min-h-screen">
	<!-- Sidebar -->
	<!-- Sidebar -->
	<!-- Sidebar -->
	<aside
		class="sticky top-24 flex h-[calc(100vh-6rem)] w-64 flex-col gap-6 overflow-y-auto border-r border-gray-200 bg-[var(--color-bg)] p-6 shadow-lg dark:border-gray-700 dark:bg-[var(--color-night)]"
	>
		<h2 class="text-3xl font-extrabold tracking-tight text-[var(--color-accent)]">Docs</h2>

		<ul class="flex flex-col gap-4">
			{#each data.docs as doc}
				<li>
					<a
						href={`/docs/${doc.slug}`}
						class="rounded-md px-3 py-2 text-[var(--color-text)] transition-all hover:bg-[var(--color-slateblue)] hover:text-white hover:shadow-md dark:text-[var(--color-slateblue)] dark:hover:bg-[var(--color-slateblue)] dark:hover:text-white"
					>
						{doc.title}
					</a>
				</li>
			{/each}
		</ul>
	</aside>

	<!-- Main Content -->
	<main class="flex-1 overflow-y-auto p-8">
		<slot />
	</main>
</div>
