<script lang="ts">
	import { onMount } from 'svelte';
	import { gsap } from 'gsap';
	import { fade } from 'svelte/transition';

	let activeIndex = 0;
	let modalOpen = false;
	let activeTab = 'summary';

	const projects = [
		// --- Federal Projects with AEM ---
		{
			title: 'G3 Drupal Website',
			category: 'Federal Work with AEM',
			cover: '/image/g3.png',
			summary: 'Led the development of a standalone site for the Generate Governance Group.',
			role: [
				'Primary point of contact for Drupal site build',
				'Designed G3 logo and deck template',
				'Migrated all content from Communities360'
			],
			tools: [
				{ name: 'Drupal', usage: 'Built custom site with new features' },
				{ name: 'Illustrator', usage: 'Logo and branding assets' },
				{ name: 'PowerPoint', usage: 'Template development' },
				{ name: 'GitHub', usage: 'Source management and documentation' }
			],
			challenges: [
				{ title: 'Legacy platform', solution: 'Custom Drupal site' },
				{ title: 'No identity', solution: 'New logo + slide templates' }
			],
			outcomes: ['Branded site launched', 'Improved stakeholder access'],
			skills: ['Drupal', 'Adobe Illustrator', 'CMS', 'Project Management'],
			images: {
				summary: '/image/g3.png',
				challenges: '/image/g3-challenges.png',
				role: '',
				tools: '',
				outcomes: '',
				skills: ''
			}
		},
		{
			title: 'Generate Documentation & Engagement',
			category: 'Federal Work with AEM',
			cover: '/image/g3-logo.svg',
			summary: 'Lead for documentation and engagement strategy on the Generate project.',
			role: [
				'Led documentation team',
				'Maintained GitBook system',
				'Integrated GitHub and GitBook',
				'Built YAML templates for Power BI dashboards'
			],
			tools: [
				{ name: 'GitBook', usage: 'Main documentation system' },
				{ name: 'GitHub', usage: 'Version control and templates' },
				{ name: 'Jira', usage: 'Agile tracking' },
				{ name: 'Discord', usage: 'Stakeholder engagement' },
				{ name: 'YAML', usage: 'Issue templates' }
			],
			challenges: [
				{ title: 'Unstructured docs', solution: 'GitBook centralization' },
				{ title: 'Low engagement', solution: 'Office Hours' }
			],
			outcomes: ['Centralized docs', 'Improved stakeholder collaboration'],
			skills: ['GitBook', 'GitHub', 'Agile', 'YAML', 'Community Management'],
			images: {
				summary: '/image/generate-summary.png',
				challenges: '',
				role: '',
				tools: '',
				outcomes: '',
				skills: ''
			}
		},
		{
			title: 'Resume Portfolio Website',
			category: 'Studio Projects',
			cover: '/image/hero1.png',
			summary: 'Designed and developed a modern portfolio site to showcase skills and work.',
			role: [
				'Built with SvelteKit + Tailwind',
				'Integrated GSAP, Markdown, and 8-bit theme toggle',
				'SEO + LLM optimized'
			],
			tools: [
				{ name: 'SvelteKit', usage: 'Frontend framework' },
				{ name: 'Tailwind CSS', usage: 'Utility-first styling' },
				{ name: 'GSAP', usage: 'Animations' },
				{ name: 'Markdown', usage: 'Content management' }
			],
			challenges: [
				{ title: 'Content structure', solution: 'Modular markdown system' },
				{ title: 'Animation performance', solution: 'GSAP timeline efficiency' }
			],
			outcomes: ['Fast-loading site', 'Highly interactive experience'],
			skills: ['SvelteKit', 'Tailwind CSS', 'GSAP', 'SEO'],
			images: {
				summary: '/image/hero1.png',
				challenges: '',
				role: '',
				tools: '',
				outcomes: '',
				skills: ''
			}
		},
		{
			title: '3D Lab',
			category: 'Studio Projects',
			cover: '/image/g3.png',
			summary: 'Designed and developed a modern portfolio site to showcase skills and work.',
			role: [
				'Built with SvelteKit + Tailwind',
				'Integrated GSAP, Markdown, and 8-bit theme toggle',
				'SEO + LLM optimized'
			],
			tools: [
				{ name: 'SvelteKit', usage: 'Frontend framework' },
				{ name: 'Tailwind CSS', usage: 'Utility-first styling' },
				{ name: 'GSAP', usage: 'Animations' },
				{ name: 'Markdown', usage: 'Content management' }
			],
			challenges: [
				{ title: 'Content structure', solution: 'Modular markdown system' },
				{ title: 'Animation performance', solution: 'GSAP timeline efficiency' }
			],
			outcomes: ['Fast-loading site', 'Highly interactive experience'],
			skills: ['SvelteKit', 'Tailwind CSS', 'GSAP', 'SEO'],
			images: {
				summary: '/image/hero1.png',
				challenges: '',
				role: '',
				tools: '',
				outcomes: '',
				skills: ''
			}
		}
		// Continue adding the rest of the projects using the same pattern...
	];

	function openModal(index: number) {
		activeIndex = index;
		activeTab = 'summary';
		modalOpen = true;
	}

	function closeModal() {
		modalOpen = false;
	}
</script>

<section class="relative w-full overflow-hidden py-12">
	<div class="flex justify-center gap-4 perspective-[1200px]">
		{#each projects as project, i}
			<button
				type="button"
				class="h-64 w-48 cursor-pointer overflow-hidden rounded-xl shadow-lg transition-transform duration-500"
				class:scale-110={i === activeIndex}
				style={`transform: perspective(1200px) rotateY(${i === activeIndex ? 0 : i < activeIndex ? -30 : 30}deg)`}
				on:click={() => openModal(i)}
			>
				<img src={project.cover} alt={project.title} class="h-full w-full object-cover" />
			</button>
		{/each}
	</div>
</section>

{#if modalOpen}
	<div
		class="fixed inset-0 z-50 flex items-center justify-center bg-black/60 backdrop-blur-md"
		transition:fade
	>
		<div
			class="relative min-h-[300px] w-full max-w-7xl rounded-xl bg-[#171123] p-6 text-white shadow-2xl"
		>
			<button on:click={closeModal} class="absolute top-3 right-4 text-xl text-white">✕</button>

			<h2 class="mb-4 text-5xl font-bold text-orange-400">{projects[activeIndex].title}</h2>

			<div class="mb-4 flex gap-4 border-b border-slate-700 pb-2">
				{#each ['summary', 'challenges', 'role', 'tools', 'outcomes', 'skills'] as tab}
					<button
						class="text-large border-b-2 pb-1 tracking-wide uppercase"
						class:border-orange-500={activeTab === tab}
						class:border-transparent={activeTab !== tab}
						on:click={() => (activeTab = tab)}>{tab}</button
					>
				{/each}
			</div>

			<div class="transition-opacity duration-300">
				{#if activeTab === 'summary'}
					{#if projects[activeIndex].images.summary}
						<img src={projects[activeIndex].images.summary} alt="Summary" class="mb-4 rounded-md" />
					{/if}
					<p class="text-lg text-slate-300">{projects[activeIndex].summary}</p>
				{:else if activeTab === 'challenges'}
					{#if projects[activeIndex].images.challenges}
						<img
							src={projects[activeIndex].images.challenges}
							alt="Challenges"
							class="mb-4 rounded-md"
						/>
					{/if}
					<ul class="space-y-2">
						{#each projects[activeIndex].challenges as ch}
							<li><strong>{ch.title}:</strong> {ch.solution}</li>
						{/each}
					</ul>
				{:else if activeTab === 'role'}
					{#if projects[activeIndex].images.role}
						<img src={projects[activeIndex].images.role} alt="Role" class="mb-4 rounded-md" />
					{/if}
					<ul class="list-disc pl-4">
						{#each projects[activeIndex].role as item}
							<li>{item}</li>
						{/each}
					</ul>
				{:else if activeTab === 'tools'}
					{#if projects[activeIndex].images.tools}
						<img src={projects[activeIndex].images.tools} alt="Tools" class="mb-4 rounded-md" />
					{/if}
					<div class="flex flex-wrap gap-2">
						{#each projects[activeIndex].tools as tool}
							<span class="rounded-full bg-slate-700 px-3 py-1 text-sm">{tool}</span>
						{/each}
					</div>
				{:else if activeTab === 'outcomes'}
					{#if projects[activeIndex].images.outcomes}
						<img
							src={projects[activeIndex].images.outcomes}
							alt="Outcomes"
							class="mb-4 rounded-md"
						/>
					{/if}
					<ul class="list-disc pl-4">
						{#each projects[activeIndex].outcomes as outcome}
							<li>{outcome}</li>
						{/each}
					</ul>
				{:else if activeTab === 'skills'}
					{#if projects[activeIndex].images.skills}
						<img src={projects[activeIndex].images.skills} alt="Skills" class="mb-4 rounded-md" />
					{/if}
					<div class="grid grid-cols-3 gap-4">
						{#each projects[activeIndex].skills as skill}
							<div class="flex items-center gap-2">
								<div class="h-6 w-6 rounded-sm bg-orange-500"></div>
								<span>{skill}</span>
							</div>
						{/each}
					</div>
				{/if}
			</div>
		</div>
	</div>
{/if}

<style>
	.perspective-\[1200px\] {
		perspective: 1200px;
	}
</style>
