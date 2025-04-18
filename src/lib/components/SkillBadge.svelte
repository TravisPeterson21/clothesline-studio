<script>
  export let icon;
  export let label;
</script>

<div class="flex items-center gap-2 px-3 py-1 rounded-full border border-[var(--color-indigo)] text-sm text-[var(--color-text)] bg-[var(--color-bg)] hover:scale-105 transition shadow-sm">
  {@html icon}
  <span>{label}</span>
</div>

  