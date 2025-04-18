<script>
	import { onMount } from 'svelte';
	import {
		Search,
		User,
		FolderKanban,
		BookText,
		Star,
		Mail,
		FileText,
		Home,
		Sun,
		Moon,
		Menu
	} from 'lucide-svelte';

	let links = [
		{ href: '/', label: 'Home', icon: Home },
		{ href: '/about', label: 'About', icon: User },
		{ href: '/projects', label: 'Projects', icon: FolderKanban },
		{ href: '/blog', label: 'Blog', icon: BookText },
		{ href: '/docs', label: 'Docs', icon: FileText },
		{ href: '/testimonials', label: 'Testimonials', icon: Star },
		{ href: '/contact', label: 'Contact', icon: Mail }
	];

	let searchQuery = '';
	let isDark = false;
	let scrolled = false;

	onMount(() => {
		const handleScroll = () => {
			scrolled = window.scrollY > 100;
		};
		window.addEventListener('scroll', handleScroll);
		return () => window.removeEventListener('scroll', handleScroll);
	});

	function toggleTheme() {
		isDark = !isDark;
		document.documentElement.classList.toggle('dark', isDark);
	}
</script>

<!-- FULL NAV (visible only when NOT scrolled) -->
{#if !scrolled}
	<nav
		class="fixed top-0 right-0 left-0 z-50 flex items-center justify-between bg-[var(--color-night)] px-6 py-4 text-white shadow-md transition-all duration-300"
	>
		<!-- Logo -->
		<a href="/" class="text-xl font-bold tracking-wide text-[var(--color-accent)]">
			Clothesline Studio
		</a>

		<!-- Center Nav Links -->
		<ul class="flex items-center gap-6 text-sm font-medium">
			{#each links as { href, label, icon }}
				<li>
					<a
						{href}
						class="group flex items-center gap-2 transition-all duration-300 ease-in-out hover:scale-105 hover:text-[var(--color-accent)]"
					>
						<svelte:component
							this={icon}
							size="18"
							class="transition-transform duration-300 group-hover:scale-125"
						/>
						<span class="relative">
							{label}
							<span
								class="absolute -bottom-1 left-0 h-[2px] w-0 bg-[var(--color-accent)] transition-all duration-300 group-hover:w-full"
							></span>
						</span>
					</a>
				</li>
			{/each}
		</ul>

		<!-- Search + Theme Toggle -->
		<div class="flex items-center gap-4">
			<div class="relative">
				<input
					type="text"
					bind:value={searchQuery}
					placeholder="Search..."
					class="rounded-md border border-[var(--color-indigo)] bg-[var(--color-bg)] px-3 py-1.5 pl-9 text-sm text-[var(--color-text)] shadow-sm transition placeholder:text-slate-400 focus:ring-2 focus:ring-[var(--color-accent)] focus:outline-none"
				/>
				<Search
					size="16"
					class="pointer-events-none absolute top-1.5 left-2 text-[var(--color-indigo)]"
				/>
			</div>

			<button
				on:click={toggleTheme}
				class="flex items-center gap-2 rounded-full border border-[var(--color-indigo)] bg-[var(--color-bg)] px-3 py-1.5 text-sm text-[var(--color-text)] shadow-sm transition hover:border-[var(--color-accent)] focus:ring-2 focus:ring-[var(--color-accent)] focus:outline-none"
				aria-label="Toggle Theme"
			>
				{#if isDark}
					<Sun size="18" />
					<span>Light</span>
				{:else}
					<Moon size="18" />
					<span>Dark</span>
				{/if}
			</button>
		</div>
	</nav>
{/if}

<!-- MINI FLOATING MENU (visible only when SCROLLED) -->
{#if scrolled}
	<div
		class="fixed top-1/2 left-6 z-50 flex -translate-y-1/2 flex-col items-center gap-4 rounded-xl bg-[var(--color-night)] p-3 shadow-lg transition-all duration-300"
	>
		<a href="/" class="text-[var(--color-accent)] transition hover:text-white">
			<Home size="24" />
		</a>
		<a href="/projects" class="text-[var(--color-accent)] transition hover:text-white">
			<FolderKanban size="24" />
		</a>
		<a href="/contact" class="text-[var(--color-accent)] transition hover:text-white">
			<Mail size="24" />
		</a>
		<button on:click={toggleTheme} class="text-[var(--color-accent)] transition hover:text-white">
			{#if isDark}
				<Sun size="24" />
			{:else}
				<Moon size="24" />
			{/if}
		</button>
	</div>
{/if}
