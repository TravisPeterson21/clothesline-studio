<script>
	import SkillBadge from '$lib/components/SkillBadge.svelte';

	const skills = [
		{ label: 'Svelte', icon: '<img src="/icons/svelte-svgrepo-com.svg" class="w-5 h-5" />' },
		{ label: 'HTML', icon: '<img src="/icons/html5-svgrepo-com.svg" class="w-5 h-5" />' },
		{ label: 'CSS', icon: '<img src="/icons/css3-svgrepo-com.svg" class="w-5 h-5" />' },
		{ label: 'GitHub', icon: '<img src="/icons/github-142-svgrepo-com.svg" class="w-5 h-5" />' },
		{
			label: 'Illustrator',
			icon: '<img src="/icons/adobe-illustrator-svgrepo-com.svg" class="w-5 h-5" />'
		},
		{
			label: 'Photoshop',
			icon: '<img src="/icons/adobe-photoshop-svgrepo-com.svg" class="w-5 h-5" />'
		},
		{
			label: 'Premiere Pro',
			icon: '<img src="/icons/adobe-premiere-svgrepo-com.svg" class="w-5 h-5" />'
		},
		{
			label: 'After Effects',
			icon: '<img src="/icons/adobe-after-effects-svgrepo-com.svg" class="w-5 h-5" />'
		},
		{ label: 'Linux', icon: '<img src="/icons/linux-svgrepo-com.svg" class="w-5 h-5" />' },
		{
			label: 'Mailchimp',
			icon: '<img src="/icons/mailchimp-svgrepo-com (1).svg" class="w-5 h-5" />'
		},
		{ label: 'Markdown', icon: '<img src="/icons/markdown-svgrepo-com.svg" class="w-5 h-5" />' },
		{ label: 'Trello', icon: '<img src="/icons/trello-svgrepo-com.svg" class="w-5 h-5" />' }
		// Add more as needed
	];
</script>

<section
	class="bg-[var(--color-bg)] px-6 py-20 text-[var(--color-text)] sm:px-12 md:px-20 lg:px-32"
>
	<div class="mx-auto max-w-6xl">
		<h2 class="mb-6 text-3xl font-bold text-[var(--color-accent)] sm:text-4xl">
			⚡ Skills & Tools
		</h2>
		<div class="flex flex-wrap gap-3">
			{#each skills as skill}
				<SkillBadge icon={skill.icon} label={skill.label} />
			{/each}
		</div>
	</div>
</section>
