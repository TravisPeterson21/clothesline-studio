<script>
	import Hero from '../lib/components/home/Hero.svelte';
	import About from '../lib/components/home/About.svelte';
	import Skills from '../lib/components/home/Skills.svelte';
	import ProjectCarousel from '../lib/components/ProjectCarousel.svelte';
	import Timeline from '../lib/components/Timeline.svelte';
	import Testimonials from '../lib/components/home/Testimonials.svelte';
	import BlogPreview from '../lib/components/home/BlogPreview.svelte';
	import CallToAction from '../lib/components/home/CallToAction.svelte';
</script>

<main>
	<Hero />
	<About />
	<ProjectCarousel />
	<Skills />

	<!-- <section class="mt-20">
    <h2 class="text-2xl font-semibold text-[var(--color-accent)] mb-8">🎓 Federal Education Projects</h2>
    <Timeline />
  </section> -->

	<Testimonials />
	<BlogPreview />
	<CallToAction />
</main>
