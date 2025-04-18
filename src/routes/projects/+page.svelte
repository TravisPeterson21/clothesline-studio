<script lang="ts">
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { ScrollTrigger } from 'gsap/ScrollTrigger';

	gsap.registerPlugin(ScrollTrigger);

	const federalProjects = [
		{
			title: 'G3 Drupal Website',
			description: 'Standalone governance site built on Drupal.',
			slug: 'g3-drupal',
			image: '/image/g3.png'
		},
		{
			title: 'CIID',
			description: 'CIID support and product development for OSEP.',
			slug: 'ciid',
			image: '/image/ciid.png'
		},
		{
			title: 'Generate',
			description: 'Special education data management solution.',
			slug: 'generate',
			image: '/image/generate.png'
		},
		{
			title: 'NCEO',
			description: 'Accessibility standards and documentation.',
			slug: 'nceo',
			image: '/image/nceo.png'
		},
		{
			title: 'CEDS',
			description: 'Standards and metadata for education data systems.',
			slug: 'ceds',
			image: '/image/ceds.png'
		},
		{
			title: 'Race to the Top-District',
			description: 'Support for personalized learning initiatives.',
			slug: 'rttd',
			image: '/image/rttd.png'
		}
	];

	const studioProjects = [
		{
			title: 'Resume / Portfolio Website',
			description:
				'A SvelteKit + Tailwind-based site to showcase technical, creative, and client projects.',
			slug: 'resume-portfolio',
			image: '/image/resume.png',
			summary: 'This is a summary of the Resume / Portfolio Website project.',
			role: 'Lead Designer and Developer',
			tools: 'SvelteKit, TailwindCSS, Vite',
			challenges: 'Responsive design, SEO optimization',
			outcomes: 'Successful launch with fast load times and positive user feedback.',
			skills: 'Front-end development, UI/UX design'
		},
		{
			title: '3D Printing Services',
			description: 'Prototyping and small-run fabrication using a custom CoreXY build.',
			slug: '3d-printing-lab',
			image: '/image/3dprintlab.png',
			summary: 'This is a summary of the 3D Printing Services project.',
			role: '3D Print Specialist',
			tools: 'Fusion 360, PrusaSlicer, OctoPrint',
			challenges: 'Print reliability, custom part production',
			outcomes: 'Created over 500 parts for clients with 98% success rate.',
			skills: '3D modeling, machine maintenance'
		},
		{
			title: 'Dog Training Products Site',
			description: 'E-commerce site for durable, field-tested training gear.',
			slug: 'dog-training-products',
			image: '/image/fallback.png',
			summary: 'This is a summary of the Dog Training Products Site project.',
			role: 'E-commerce Developer',
			tools: 'Shopify, Liquid, TailwindCSS',
			challenges: 'Inventory management, customer engagement',
			outcomes: 'Increased sales by 40% within first quarter.',
			skills: 'E-commerce development, marketing strategy'
		}
	];

	const clientProjects = [
		{
			title: 'Saw Dogs Portland',
			description:
				'Site for a family-run lawn and tree business. Optimized for local SEO, speed, and easy client updates.',
			slug: 'saw-dogs-portland',
			image: '/image/fallback.png',
			summary: 'This is a summary of the Saw Dogs Portland project.',
			role: 'Web Developer and SEO Specialist',
			tools: 'SvelteKit, TailwindCSS, Vercel',
			challenges: 'Local SEO optimization, fast deployment',
			outcomes: 'Ranked top 3 on Google for local keywords.',
			skills: 'SEO, web development'
		}
	];

	let activeProject = null;
	let modalOpen = false;
	let activeTab = 'summary';

	function openModal(project) {
		activeProject = project;
		modalOpen = true;
		activeTab = 'summary';
	}

	function closeModal() {
		modalOpen = false;
		activeProject = null;
	}

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

<section class="mx-auto max-w-6xl px-6 py-20 text-[var(--color-text)]">
	<h1 class="mb-8 text-5xl font-bold text-[var(--color-accent)]">Selected Work</h1>
	<p class="mb-16 max-w-2xl text-lg opacity-80">
		A cross-disciplinary look at 10+ years of experience in design, development, accessibility, and
		education systems.
	</p>

	<div class="space-y-16">
		<!-- Federal Education Projects -->
		<div>
			<h2 class="mb-6 text-3xl font-semibold text-[var(--color-accent)]">
				Federal Education Work (AEM)
			</h2>
			<div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
				{#each federalProjects as project}
					<div
						on:click={() => openModal(project)}
						class="project-card group relative flex cursor-pointer flex-col overflow-hidden rounded-2xl border border-[var(--color-indigo)] bg-[var(--color-bg)] shadow-lg transition-transform hover:scale-105 hover:shadow-2xl"
					>
						<img
							src={project.image}
							alt={project.title}
							on:error={(e) => (e.target.src = '/image/fallback.png')}
							class="h-48 w-full object-cover"
						/>
						<div class="p-5">
							<h3 class="mb-1 text-xl font-bold text-[var(--color-accent)] group-hover:underline">
								{project.title}
							</h3>
							<p class="text-sm text-[var(--color-slateblue)] opacity-80">
								{project.description}
							</p>
						</div>
					</div>
				{/each}
			</div>
		</div>
		<!-- Studio Projects -->
		<div>
			<h2 class="mb-6 text-3xl font-semibold text-[var(--color-accent)]">Studio Projects</h2>
			<div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
				{#each studioProjects as project}
					<div
						on:click={() => openModal(project)}
						class="project-card group relative flex cursor-pointer flex-col overflow-hidden rounded-2xl border border-[var(--color-plum)] bg-[var(--color-bg)] shadow-lg transition-transform hover:scale-105 hover:shadow-2xl"
					>
						<img
							src={project.image}
							alt={project.title}
							on:error={(e) => (e.target.src = '/image/resume.png')}
							class="h-48 w-full object-cover"
						/>
						<div class="p-5">
							<h3 class="mb-1 text-xl font-bold text-[var(--color-accent)] group-hover:underline">
								{project.title}
							</h3>
							<p class="text-sm text-[var(--color-slateblue)] opacity-80">
								{project.description}
							</p>
						</div>
					</div>
				{/each}
			</div>
		</div>

		<!-- Client Projects -->
		<div>
			<h2 class="mb-6 text-3xl font-semibold text-[var(--color-accent)]">Client Projects</h2>
			<div class="grid gap-8 sm:grid-cols-2 lg:grid-cols-3">
				{#each clientProjects as project}
					<div
						on:click={() => openModal(project)}
						class="project-card group relative flex cursor-pointer flex-col overflow-hidden rounded-2xl border border-[var(--color-indigo)] bg-[var(--color-bg)] shadow-lg transition-transform hover:scale-105 hover:shadow-2xl"
					>
						<img
							src={project.image}
							alt={project.title}
							on:error={(e) => (e.target.src = '/image/fallback.png')}
							class="h-48 w-full object-cover"
						/>
						<div class="p-5">
							<h3 class="mb-1 text-xl font-bold text-[var(--color-accent)] group-hover:underline">
								{project.title}
							</h3>
							<p class="text-sm text-[var(--color-slateblue)] opacity-80">
								{project.description}
							</p>
						</div>
					</div>
				{/each}
			</div>
		</div>
	</div>

	<!-- Modal -->
	{#if modalOpen}
		<div
			class="fixed inset-0 z-50 flex items-center justify-center bg-black/70 backdrop-blur"
			on:click={closeModal}
		>
			<div
				class="relative w-full max-w-2xl rounded-xl bg-[var(--color-bg)] p-8 text-[var(--color-text)] shadow-2xl"
				on:click|stopPropagation
			>
				<button
					on:click={closeModal}
					class="absolute top-4 right-4 text-2xl text-[var(--color-accent)] hover:text-red-500"
				>
					&times;
				</button>
				<img
					src={activeProject.image}
					alt={activeProject.title}
					class="mb-6 h-60 w-full rounded-md object-cover"
				/>
				<h2 class="mb-4 text-3xl font-bold text-[var(--color-accent)]">
					{activeProject.title}
				</h2>
				<div class="mb-4 flex space-x-4">
					{#each ['summary', 'role', 'tools', 'challenges', 'outcomes', 'skills'] as tab}
						<button
							on:click={() => (activeTab = tab)}
							class="rounded-full border px-3 py-1 text-sm transition hover:bg-[var(--color-accent)] hover:text-white"
						>
							{tab.charAt(0).toUpperCase() + tab.slice(1)}
						</button>
					{/each}
				</div>
				<p class="text-lg opacity-80">{activeProject[activeTab]}</p>
			</div>
		</div>
	{/if}
</section>
