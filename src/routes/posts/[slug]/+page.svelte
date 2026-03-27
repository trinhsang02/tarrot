<script lang="ts">
  import type { PageData } from "./$types";

  let { data }: { data: PageData } = $props();
</script>

<section class="space-y-3">
  <p class="theme-accent text-xs uppercase tracking-[0.2em]">Dynamic Route</p>
  <h1 class="text-3xl font-semibold">Post: {data.slug}</h1>
  <p class="theme-muted">
    This page is rendered by
    <span class="theme-code font-mono">src/routes/posts/[slug]/+page.svelte</span>
    and receives the URL parameter from
    <span class="theme-code font-mono">+page.ts</span>.
  </p>
</section>
