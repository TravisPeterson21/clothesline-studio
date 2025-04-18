<script>
  import { onMount } from 'svelte';
  import AccessibilityPanel from './AccessibilityPanel.svelte';
  import { writable } from 'svelte/store';

  const showPanel = writable(false);
</script>

<div class="fixed bottom-4 right-4 z-50">
  <button
    on:click={() => showPanel.update(v => !v)}
    class="bg-[var(--color-accent)] text-white font-semibold px-4 py-2 rounded-full shadow hover:bg-orange-600 transition"
  >
    ♿ Accessibility
  </button>

  {#if $showPanel}
    <AccessibilityPanel on:close={() => showPanel.set(false)} />
  {/if}
</div>
