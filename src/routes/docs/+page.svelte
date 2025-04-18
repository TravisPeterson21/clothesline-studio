<script lang="ts">
	export let data: { docs: { slug: string; title: string }[] };
</script>

<section class="mx-auto max-w-3xl p-8">
	<h1 class="mb-8 text-4xl font-bold">Documentation</h1>

	<ul class="space-y-4">
		{#each data.docs as doc}
			<li>
				<a class="text-xl text-blue-500 hover:underline" href={`/docs/${doc.slug}`}>
					{doc.title}
				</a>
			</li>
		{/each}
	</ul>
</section>
