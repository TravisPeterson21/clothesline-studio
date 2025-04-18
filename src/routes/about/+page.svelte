<script>
  import { onMount } from 'svelte';
  import { gsap } from 'gsap';
  import { ScrollTrigger } from 'gsap/ScrollTrigger';
  import { Code2, Book, Settings, Printer, Users } from 'lucide-svelte';

  gsap.registerPlugin(ScrollTrigger); // ✅ This line is key!

  onMount(() => {
    gsap.utils.toArray('.card').forEach((card) => {
      gsap.from(card, {
        scrollTrigger: {
          trigger: card,
          start: 'top 80%',
          toggleActions: 'play none none none',
        },
        opacity: 0,
        y: 40,
        duration: 0.6,
        ease: 'power2.out'
      });
    });

    gsap.utils.toArray('.skill-icon').forEach((icon, i) => {
      gsap.from(icon, {
        scrollTrigger: {
          trigger: icon,
          start: 'top 90%',
          toggleActions: 'play none none none',
        },
        opacity: 0,
        scale: 0.8,
        duration: 0.4,
        delay: i * 0.05,
        ease: 'back.out(1.7)'
      });
    });
  });

  const skills = [
    { icon: Code2, label: 'Web Dev' },
    { icon: Settings, label: '508/WCAG' },
    { icon: Book, label: 'Docs & GitBook' },
    { icon: Printer, label: '3D Printing' },
    { icon: Users, label: 'Client Collab' }
  ];
</script>

<section class="py-16 px-4 text-[var(--color-text)]">
  <div class="max-w-5xl mx-auto grid lg:grid-cols-3 gap-10">
    <!-- 📸 Profile / Studio Image -->
    <div class="flex justify-center items-start">
      <div class="rounded-3xl overflow-hidden shadow-xl w-64 h-64 bg-[var(--color-plum)] text-center flex items-center justify-center text-[var(--color-slateblue)] text-sm">
        [ Your Photo or Ripley Pic ]
      </div>
    </div>

    <!-- 🧠 Intro & Background -->
    <div class="lg:col-span-2 space-y-6 text-lg leading-relaxed">
      <h1 class="text-4xl font-bold text-[var(--color-accent)]">Hi, I'm Travis</h1>
      <p>
        I'm a creative technologist and digital systems builder based in Montana. I blend design,
        frontend development, documentation strategy, and accessibility into powerful, practical
        products and websites.
      </p>
      <p>
        For over a decade, I worked as a consultant for AEM Corporation, helping U.S. Department of
        Education projects achieve their goals through accessible, well-documented, and thoughtfully
        designed digital experiences.
      </p>
    </div>
  </div>

  <!-- 🧩 Experience Cards -->
  <div class="max-w-5xl mx-auto mt-16 grid sm:grid-cols-2 gap-8">
    <div class="card p-6 bg-[var(--color-bg)] border border-[var(--color-plum)] rounded-xl shadow transition">
      <h2 class="text-xl font-semibold text-[var(--color-accent)] mb-2">Federal Work Highlights</h2>
      <ul class="list-disc list-inside space-y-1 text-sm text-[var(--color-slateblue)]">
        <li><strong>CIID:</strong> Special education data integration</li>
        <li><strong>CEDS:</strong> Data standards + toolkits</li>
        <li><strong>ERIC:</strong> Accessible frontend design</li>
        <li><strong>NCEO:</strong> Web strategy for academic resources</li>
      </ul>
    </div>

    <div class="card p-6 bg-[var(--color-bg)] border border-[var(--color-indigo)] rounded-xl shadow transition">
      <h2 class="text-xl font-semibold text-[var(--color-accent)] mb-2">Outside the Screen</h2>
      <p class="text-sm text-[var(--color-slateblue)]">
        When I'm not building, I’m out with Ripley (my golden retriever), testing gear, or prototyping weird ideas for the studio.
      </p>
      <p class="mt-2 font-semibold text-[var(--color-accent)]">
        Let’s build something useful, beautiful, or at least fun.
      </p>
    </div>
  </div>

  <!-- 🚀 Skills Section -->
  <div class="max-w-5xl mx-auto mt-20">
    <h2 class="text-2xl font-semibold text-[var(--color-accent)] mb-6">🔧 Studio Skills</h2>
    <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-6 text-center">
      {#each skills as skill}
        <div class="skill-icon flex flex-col items-center justify-center p-4 bg-[var(--color-bg)] rounded-lg shadow border border-[var(--color-slateblue)] hover:scale-105 transition">
          <svelte:component this={skill.icon} size="32" class="text-[var(--color-accent)] mb-2" />
          <span class="text-sm text-[var(--color-slateblue)]">{skill.label}</span>
        </div>
      {/each}
    </div>
  </div>
</section>


  