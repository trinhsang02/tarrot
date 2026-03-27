<script lang="ts">
  import "../app.css";
  import { onMount } from "svelte";
  import Navbar from "../components/navbar.svelte";

  type ThemePreference = "light" | "dark" | "system";

  let themePreference: ThemePreference = "system";
  let resolvedTheme: "light" | "dark" = "light";

  const isThemePreference = (value: string | null): value is ThemePreference => {
    return value === "light" || value === "dark" || value === "system";
  };

  const applyTheme = (preference: ThemePreference) => {
    const systemPrefersDark = window.matchMedia("(prefers-color-scheme: dark)").matches;

    resolvedTheme =
      preference === "system" ? (systemPrefersDark ? "dark" : "light") : preference;

    document.documentElement.classList.toggle("dark", resolvedTheme === "dark");
    document.documentElement.dataset.theme = resolvedTheme;
  };

  const setTheme = (preference: ThemePreference) => {
    themePreference = preference;
    localStorage.setItem("theme-preference", preference);
    applyTheme(preference);
  };

  onMount(() => {
    const storedTheme = localStorage.getItem("theme-preference");

    if (isThemePreference(storedTheme)) {
      themePreference = storedTheme;
    }

    applyTheme(themePreference);

    const media = window.matchMedia("(prefers-color-scheme: dark)");
    const handleSystemThemeChange = () => {
      if (themePreference === "system") {
        applyTheme("system");
      }
    };

    media.addEventListener("change", handleSystemThemeChange);

    return () => {
      media.removeEventListener("change", handleSystemThemeChange);
    };
  });
</script>

<div class="app-shell min-h-screen">
  <header class="app-header border-b backdrop-blur">
    <nav class="mx-auto flex max-w-5xl items-center gap-6 px-4 py-4 text-sm">
      <a class="theme-accent font-semibold" href="/">Tarrot</a>

      <div class="ml-auto flex items-center gap-2">
        <button
          class="theme-toggle rounded-md px-2 py-1 text-xs"
          on:click={() => setTheme("light")}
          aria-pressed={themePreference === "light"}
          type="button"
        >
          Light
        </button>
        <button
          class="theme-toggle rounded-md px-2 py-1 text-xs"
          on:click={() => setTheme("dark")}
          aria-pressed={themePreference === "dark"}
          type="button"
        >
          Dark
        </button>
        <button
          class="theme-toggle rounded-md px-2 py-1 text-xs"
          on:click={() => setTheme("system")}
          aria-pressed={themePreference === "system"}
          title={`Following ${resolvedTheme} system theme`}
          type="button"
        >
          System
        </button>
      </div>
    </nav>
  </header>

  <main class="mx-auto max-w-5xl px-4 py-10">
    <slot />
  </main>

  <footer>
    <Navbar />
  </footer>
</div>
