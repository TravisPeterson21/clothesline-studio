<script>
  export let data;
</script>

<section class="max-w-3xl mx-auto py-12">
  <h1 class="text-4xl font-bold mb-6">Blog</h1>

  <ul class="space-y-4">
    {#each data.posts as post}
      <li>
        <a href={`/blog/${post.slug}`} class="text-orange-500 text-xl hover:underline">
          {post.metadata.title}
        </a>
        <p class="text-slate-400 text-sm">{post.metadata.date}</p>
        <p class="text-slate-600">{post.metadata.description}</p>
      </li>
    {/each}
  </ul>
</section>


  