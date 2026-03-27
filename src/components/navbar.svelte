<script lang="ts">
    import { faClockRotateLeft, faUser, faHome } from "@fortawesome/free-solid-svg-icons";
    import Icon from "./Icon.svelte";
</script>

<nav aria-label="Primary navigation" class="mx-auto max-w-5xl px-4 pb-5">
    <div class="theme-card flex items-center justify-evenly gap-5 rounded-xl border px-4 py-3 text-sm">
        <a class="theme-link flex flex-col items-center gap-1" href="/">
            <Icon icon={faHome} size={18} />
            <span>Home</span>
        </a>

        <a class="theme-link flex flex-col items-center gap-1" href="/about">
            <Icon icon={faClockRotateLeft} size={18} />
            <span>History</span>
        </a>

        <a class="theme-link flex flex-col items-center gap-1" href="/contact">
            <Icon icon={faUser} size={18} />
            <span>Contact</span>
        </a>
    </div>
</nav>