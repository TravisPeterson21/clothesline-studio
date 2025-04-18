<script lang="ts">
    export let data;
    const { content, metadata } = data;
  </script>
  
  <svelte:head>
    <title>{metadata.title}</title>
  </svelte:head>
  
  <article class="prose lg:prose-xl mx-auto p-6">
    <h1>{metadata.title}</h1>
    <p class="text-gray-500 italic">{metadata.date}</p>
    <svelte:component this={content} />
  </article>
  