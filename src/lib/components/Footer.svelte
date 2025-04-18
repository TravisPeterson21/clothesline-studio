<script>
  import { Github, Linkedin, Instagram, Youtube } from 'lucide-svelte';
</script>

<footer class="bg-[var(--color-night)] text-white text-sm mt-10 px-6 py-10 transition-colors duration-300">
  <div class="max-w-6xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-6 sm:gap-0">
    
    <!-- Left: Copyright -->
    <p class="text-center sm:text-left">
      &copy; {new Date().getFullYear()} Clothesline Studio · Built by Travis in Montana 🏔️
    </p>

    <!-- Center: Legal Links -->
    <div class="flex gap-4">
      <a href="/sitemap" class="hover:text-[var(--color-accent)] transition">Sitemap</a>
      <a href="/accessibility" class="hover:text-[var(--color-accent)] transition">Accessibility</a>
      <a href="/llm-optimization" class="hover:text-[var(--color-accent)] transition">LLM</a>
    </div>

    <!-- Right: Social Links -->
    <div class="flex gap-4">
      <a href="https://www.linkedin.com/in/travis-profile" target="_blank" rel="noopener noreferrer" class="hover:text-[var(--color-accent)] transition">
        <Linkedin size="18" />
      </a>
      <a href="https://github.com/travisprofile" target="_blank" rel="noopener noreferrer" class="hover:text-[var(--color-accent)] transition">
        <Github size="18" />
      </a>
      <a href="https://bsky.app/profile/travis.bsky.social" target="_blank" rel="noopener noreferrer" class="hover:text-[var(--color-accent)] transition">
        <span class="font-bold text-lg">𝕓</span>
      </a>
      <a href="https://instagram.com/travisstudio" target="_blank" rel="noopener noreferrer" class="hover:text-[var(--color-accent)] transition">
        <Instagram size="18" />
      </a>
      <a href="https://youtube.com/@travisstudio" target="_blank" rel="noopener noreferrer" class="hover:text-[var(--color-accent)] transition">
        <Youtube size="18" />
      </a>
    </div>
  </div>
</footer>

  