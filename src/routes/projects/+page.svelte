<script lang="ts">
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';

	gsap.registerPlugin(ScrollTrigger);

	const studioProjects = [
		{
			title: 'Resume / Portfolio Website',
			description:
				'A SvelteKit + Tailwind-based site to showcase technical, creative, and client projects.',
			slug: 'resume-portfolio',
			image: '/image/resume.png'
		},
		{
			title: '3D Printing Services',
			description: 'Prototyping and small-run fabrication using a custom CoreXY build.',
			slug: '3d-printing-lab',
			image: '/image/3dprintlab.png'
		},
		{
			title: 'Dog Training Products Site',
			description: 'E-commerce site for durable, field-tested training gear.',
			slug: 'dog-training-products',
			image: '/image/fallback.png'
		}
	];

	const clientProjects = [
		{
			title: 'Saw Dogs Portland',
			description:
				'Site for a family-run lawn and tree business. Optimized for local SEO, speed, and easy client updates.',
			slug: 'saw-dogs-portland',
			image: '/image/fallback.png'
		}
	];

	onMount(() => {
		gsap.utils.toArray('.project-card').forEach((card) => {
			gsap.from(card, {
				scrollTrigger: {
					trigger: card,
					start: 'top 85%',
					toggleActions: 'play none none none'
				},
				opacity: 0,
				y: 30,
				duration: 0.6,
				ease: 'power2.out'
			});
		});
	});
</script>

<section class="mx-auto max-w-5xl px-4 py-16 text-[var(--color-text)]">
	<h1 class="mb-6 text-4xl font-bold text-[var(--color-accent)]">Selected Work</h1>
	<p class="mb-10 max-w-2xl text-lg">
		A cross-disciplinary look at 10+ years of experience in design, development, accessibility, and
		education systems.
	</p>

	<!-- Studio Projects -->
	<div class="mb-20">
		<h2 class="mb-4 text-2xl font-semibold text-[var(--color-accent)]">🎨 Studio Projects</h2>
		<div class="grid gap-8 sm:grid-cols-2">
			{#each studioProjects as project}
				<a
					href={`/projects/${project.slug}`}
					class="project-card group block overflow-hidden rounded-xl border border-[var(--color-plum)] bg-[var(--color-bg)] shadow-md transition duration-300 hover:border-[var(--color-accent)] hover:shadow-xl"
				>
					<img
						src={project.image}
						alt={project.title}
						on:error={(e) => (e.target.src = '/image/resume.png')}
						class="w-full object-cover transition-transform duration-300 group-hover:scale-105"
					/>
					<div class="p-5">
						<h3 class="mb-1 text-xl font-semibold text-[var(--color-accent)] group-hover:underline">
							{project.title}
						</h3>
						<p class="text-sm text-[var(--color-slateblue)]">{project.description}</p>
					</div>
				</a>
			{/each}
		</div>
	</div>

	<!-- Client Projects -->
	<div class="mb-20">
		<h2 class="mb-4 text-2xl font-semibold text-[var(--color-accent)]">🛠 Client Projects</h2>
		<div class="grid gap-8 sm:grid-cols-2">
			{#each clientProjects as project}
				<a
					href={`/projects/${project.slug}`}
					class="project-card group block overflow-hidden rounded-xl border border-[var(--color-indigo)] bg-[var(--color-bg)] shadow-md transition duration-300 hover:border-[var(--color-accent)] hover:shadow-xl"
				>
					<img
						src={project.image}
						alt={project.title}
						on:error={(e) => (e.target.src = '/image/fallback.png')}
						class="h-48 w-full object-cover transition-transform duration-300 group-hover:scale-105"
					/>
					<div class="p-5">
						<h3 class="mb-1 text-xl font-semibold text-[var(--color-accent)] group-hover:underline">
							{project.title}
						</h3>
						<p class="text-sm text-[var(--color-slateblue)]">{project.description}</p>
					</div>
				</a>
			{/each}
		</div>
	</div>

	<!-- Federal Education Work -->
	<div>
		<h2 class="mb-4 text-2xl font-semibold text-[var(--color-accent)]">
			🎓 Federal Education Work (AEM)
		</h2>
		<p class="mb-8 text-sm text-[var(--color-slateblue)]">
			Long-term engagement with the U.S. Department of Education via AEM Corporation. Full case
			studies coming soon — highlights from CIID, CEDS, ERIC, NCEO, and Generate will be available
			as standalone pages.
		</p>

		<!-- This area can be replaced with a new ProjectCards viewer -->
		<div class="rounded-xl bg-[var(--color-night)] p-8 text-slate-300">
			<p class="italic">Case study modules in development.</p>
		</div>
	</div>
</section>
