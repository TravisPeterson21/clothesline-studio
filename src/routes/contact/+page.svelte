<script lang="ts">
	import { Mail, Github, Linkedin, MessageCircle } from 'lucide-svelte';

	let name = '';
	let email = '';
	let message = '';
	let submitting = false;
	let success = false;
	let error = '';

	const handleSubmit = async (e: Event) => {
		e.preventDefault();
		submitting = true;
		success = false;
		error = '';

		try {
			// Simulate sending to an API or service
			await new Promise((r) => setTimeout(r, 1000));

			if (!name || !email || !message) {
				throw new Error('All fields are required.');
			}

			success = true;
			name = '';
			email = '';
			message = '';
		} catch (err) {
			error = err instanceof Error ? err.message : 'Something went wrong.';
		} finally {
			submitting = false;
		}
	};
</script>

<section class="mx-auto max-w-xl px-4 py-16">
	<h1 class="mb-4 text-3xl font-bold text-orange-400">Get in Touch</h1>
	<p class="mb-6 text-slate-300">
		Interested in working together? Want to chat about a project, idea, or collaboration? Drop me a
		message below, or find me on social.
	</p>

	<form on:submit|preventDefault={handleSubmit} class="space-y-6">
		<div>
			<label for="name" class="block text-sm font-medium text-slate-200">Name</label>
			<input
				id="name"
				type="text"
				bind:value={name}
				required
				class="mt-1 block w-full rounded-md border border-slate-700 bg-slate-800 p-2 text-white placeholder-slate-400 focus:ring-2 focus:ring-orange-400 focus:outline-none"
				placeholder="Your Name"
			/>
		</div>

		<div>
			<label for="email" class="block text-sm font-medium text-slate-200">Email</label>
			<input
				id="email"
				type="email"
				bind:value={email}
				required
				class="mt-1 block w-full rounded-md border border-slate-700 bg-slate-800 p-2 text-white placeholder-slate-400 focus:ring-2 focus:ring-orange-400 focus:outline-none"
				placeholder="you@example.com"
			/>
		</div>

		<div>
			<label for="message" class="block text-sm font-medium text-slate-200">Message</label>
			<textarea
				id="message"
				rows="5"
				bind:value={message}
				required
				class="mt-1 block w-full rounded-md border border-slate-700 bg-slate-800 p-2 text-white placeholder-slate-400 focus:ring-2 focus:ring-orange-400 focus:outline-none"
				placeholder="What's on your mind?"
			></textarea>
		</div>

		<button
			type="submit"
			class="rounded-md bg-orange-500 px-4 py-2 font-semibold text-white transition-colors hover:bg-orange-600 disabled:opacity-60"
			disabled={submitting}
		>
			{submitting ? 'Sending…' : 'Send Message'}
		</button>

		{#if success}
			<p class="text-sm text-green-400">Thanks! Your message was sent successfully.</p>
		{/if}
		{#if error}
			<p class="text-sm text-red-400">Error: {error}</p>
		{/if}
	</form>

	<div class="mt-12 text-slate-300">
		<p class="mb-4">Or find me on:</p>
		<div class="flex space-x-6 text-orange-400">
			<a href="https://github.com/yourusername" target="_blank" aria-label="GitHub">
				<Github class="h-6 w-6" />
			</a>
			<a href="https://linkedin.com/in/yourusername" target="_blank" aria-label="LinkedIn">
				<Linkedin class="h-6 w-6" />
			</a>
			<a href="https://discordapp.com/users/yourdiscordid" target="_blank" aria-label="Discord">
				<MessageCircle class="h-6 w-6" />
			</a>
			<a href="mailto:you@example.com" aria-label="Email">
				<Mail class="h-6 w-6" />
			</a>
		</div>
	</div>
</section>
