<script>
  import { Mail, Github, Linkedin, MessageCircle } from 'lucide-svelte';

  let name = '';
  let email = '';
  let message = '';
  let submitting = false;
  let success = false;
  let error = '';

  const handleSubmit = async (e) => {
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
      error = err.message || 'Something went wrong.';
    } finally {
      submitting = false;
    }
  };
</script>

<section class="max-w-xl mx-auto py-16 px-4">
  <h1 class="text-3xl font-bold text-orange-400 mb-4">Get in Touch</h1>
  <p class="text-slate-300 mb-6">
    Interested in working together? Want to chat about a project, idea, or collaboration?
    Drop me a message below, or find me on social.
  </p>

  <form on:submit|preventDefault={handleSubmit} class="space-y-6">
    <div>
      <label for="name" class="block text-sm font-medium text-slate-200">Name</label>
      <input
        id="name"
        type="text"
        bind:value={name}
        required
        class="mt-1 block w-full rounded-md bg-slate-800 border border-slate-700 p-2 text-white placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-orange-400"
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
        class="mt-1 block w-full rounded-md bg-slate-800 border border-slate-700 p-2 text-white placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-orange-400"
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
        class="mt-1 block w-full rounded-md bg-slate-800 border border-slate-700 p-2 text-white placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-orange-400"
        placeholder="What's on your mind?"
      ></textarea>
    </div>
  
    <button
      type="submit"
      class="bg-orange-500 hover:bg-orange-600 text-white font-semibold py-2 px-4 rounded-md transition-colors disabled:opacity-60"
      disabled={submitting}
    >
      {submitting ? 'Sending…' : 'Send Message'}
    </button>
  
    {#if success}
      <p class="text-green-400 text-sm">Thanks! Your message was sent successfully.</p>
    {/if}
    {#if error}
      <p class="text-red-400 text-sm">Error: {error}</p>
    {/if}
  </form>
  

  <div class="mt-12 text-slate-300">
    <p class="mb-4">Or find me on:</p>
    <div class="flex space-x-6 text-orange-400">
      <a href="https://github.com/yourusername" target="_blank" aria-label="GitHub">
        <Github class="w-6 h-6" />
      </a>
      <a href="https://linkedin.com/in/yourusername" target="_blank" aria-label="LinkedIn">
        <Linkedin class="w-6 h-6" />
      </a>
      <a href="https://discordapp.com/users/yourdiscordid" target="_blank" aria-label="Discord">
        <MessageCircle class="w-6 h-6" />
      </a>
      <a href="mailto:you@example.com" aria-label="Email">
        <Mail class="w-6 h-6" />
      </a>
    </div>
  </div>
</section>




  