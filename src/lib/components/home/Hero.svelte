<script>
	import { ArrowRight } from 'lucide-svelte';
</script>

<section
	class="bg-[var(--color-bg)] px-6 py-24 text-[var(--color-text)] transition-colors duration-300 sm:px-12 md:px-20 lg:px-32"
>
	<div class="mx-auto flex max-w-6xl flex-col-reverse items-center gap-16 md:flex-row md:gap-24">
		<!-- Text Content -->
		<div class="flex-2 space-y-6 text-center md:text-left">
			<h1 class="text-4xl leading-tight font-extrabold tracking-tight sm:text-5xl">
				Hi, I'm <span class="text-[var(--color-accent)]">Travis</span><br />
				Creative technologist, strategist, and maker.
			</h1>
			<p class="mx-auto max-w-xl text-lg text-[var(--color-indigo)] md:mx-0">
				I help organizations and ideas shine online — from concept to code.
			</p>
			<div class="mt-6 flex flex-col justify-center gap-4 sm:flex-row md:justify-start">
				<a
					href="/projects"
					class="rounded-xl bg-[var(--color-accent)] px-6 py-3 font-semibold text-white shadow transition hover:scale-105 hover:shadow-lg"
				>
					View My Work
				</a>
				<a
					href="/about"
					class="rounded-xl border border-[var(--color-accent)] px-6 py-3 font-medium text-[var(--color-accent)] transition hover:bg-[var(--color-accent)] hover:text-white"
				>
					About Me
				</a>
			</div>
		</div>

		<!-- Hero Image -->
		<div class="flex flex-1 justify-center md:justify-end">
			<div
				class="h-[22rem] w-[22rem] overflow-hidden rounded-[2rem] border-4 border-[var(--color-indigo)] bg-[var(--color-plum)] shadow-2xl sm:h-[26rem] sm:w-[26rem] md:h-[28rem] md:w-[28rem]"
			>
				<img
					src="/image/hero1.png"
					alt="Travis and Ripley on a creative journey"
					class="h-full w-full object-cover"
				/>
			</div>
		</div>
	</div>
</section>
