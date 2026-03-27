<section class="space-y-4">
  <p class="theme-accent text-xs uppercase tracking-[0.2em]">SvelteKit Routing</p>
  <h1 class="text-4xl font-bold">Basic Route Setup</h1>
  <p class="theme-muted max-w-2xl">
    This app now uses folder-based routing. Add new pages by creating
    <span class="theme-code font-mono">+page.svelte</span>
    files inside folders under
    <span class="theme-code font-mono">src/routes</span>.
  </p>

  <div class="grid gap-3 pt-4 sm:grid-cols-3">
    <a class="theme-card rounded-lg border p-4" href="/about">/about</a>
    <a class="theme-card rounded-lg border p-4" href="/contact">/contact</a>
    <a class="theme-card rounded-lg border p-4" href="/posts/first-post">/posts/[slug]</a>
  </div>
</section>
