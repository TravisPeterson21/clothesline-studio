<script>
  import { Code, Layers, Compass } from 'lucide-svelte';
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';

  onMount(async () => {
    const { ScrollTrigger } = await import('gsap/ScrollTrigger');
    gsap.registerPlugin(ScrollTrigger);

    gsap.utils.toArray('.about-card').forEach((card) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: 'top 85%',
          toggleActions: 'play none none none',
        },
        opacity: 0,
        y: 40,
        duration: 0.6,
        ease: 'power2.out'
      });
    });
  });
</script>


<section class="bg-[var(--color-bg)] text-[var(--color-text)] py-20 px-6 sm:px-12 md:px-20 lg:px-32 transition-colors duration-300">
  <div class="max-w-5xl mx-auto text-center space-y-8">
    
    <h2 class="text-3xl sm:text-4xl font-bold text-[var(--color-accent)]">
      What I Do
    </h2>
    
    <p class="text-lg text-[var(--color-slateblue)] max-w-3xl mx-auto">
      With a background in consulting and a passion for design and development, I build beautiful, functional tools for teams, products, and people.
    </p>

    <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-8 mt-10">
      <!-- Creative Direction -->
      <div class="about-card bg-[var(--color-bg)] rounded-xl shadow-md p-6 space-y-3 border border-[var(--color-plum)] hover:shadow-lg transition">
        <Compass class="w-8 h-8 text-[var(--color-accent)]" />
        <h3 class="text-xl font-semibold">Creative Direction</h3>
        <p class="text-sm text-[var(--color-text)]">
          Story-driven design, visual systems, and bold concepts grounded in clarity.
        </p>
      </div>

      <!-- Front-End Dev -->
      <div class="about-card bg-[var(--color-bg)] rounded-xl shadow-md p-6 space-y-3 border border-[var(--color-plum)] hover:shadow-lg transition">
        <Code class="w-8 h-8 text-[var(--color-accent)]" />
        <h3 class="text-xl font-semibold">Front-End Development</h3>
        <p class="text-sm text-[var(--color-text)]">
          Svelte, Tailwind, GSAP, and custom UI for modern, blazing-fast experiences.
        </p>
      </div>

      <!-- System Design -->
      <div class="about-card bg-[var(--color-bg)] rounded-xl shadow-md p-6 space-y-3 border border-[var(--color-plum)] hover:shadow-lg transition">
        <Layers class="w-8 h-8 text-[var(--color-accent)]" />
        <h3 class="text-xl font-semibold">System Design</h3>
        <p class="text-sm text-[var(--color-text)]">
          PM workflows, documentation, integration strategy, and project tooling.
        </p>
      </div>
    </div>
  </div>
</section>

  
  