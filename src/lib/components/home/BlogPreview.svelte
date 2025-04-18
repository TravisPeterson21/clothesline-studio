<script>
  const posts = [
    {
      title: "The Value of Design Systems in Public Sector Work",
      date: "March 18, 2025",
      summary: "How consistent patterns and tools can help teams ship faster and communicate better.",
      link: "#",
    },
    {
      title: "Why I Moved from DecapCMS to Sanity",
      date: "April 4, 2025",
      summary: "A quick look at why schema-first content management just makes sense for modern sites.",
      link: "#",
    }
  ];
</script>

<section class="bg-[var(--color-bg)] text-[var(--color-text)] py-20 px-6 sm:px-12 md:px-20 lg:px-32 transition-colors duration-300">
  <div class="max-w-6xl mx-auto space-y-16">
    <!-- Header -->
    <div class="text-center space-y-3">
      <h2 class="text-3xl sm:text-4xl font-bold text-[var(--color-accent)]">Latest Insights</h2>
      <p class="text-lg text-[var(--color-slateblue)]">Notes on design, dev, and digital craft.</p>
    </div>

    <!-- Blog Cards -->
    <div class="grid gap-8 sm:grid-cols-2">
      {#each posts as post}
        <a href={post.link} class="group block bg-[var(--color-bg)] border border-[var(--color-plum)] p-6 rounded-xl shadow hover:shadow-xl hover:border-[var(--color-accent)] transition duration-300">
          <div class="space-y-2">
            <h3 class="text-xl font-semibold text-[var(--color-accent)] group-hover:underline">{post.title}</h3>
            <p class="text-sm text-[var(--color-slateblue)]">{post.date}</p>
            <p class="text-sm text-[var(--color-text)] mt-2">{post.summary}</p>
          </div>
        </a>
      {/each}
    </div>
  </div>
</section>

  