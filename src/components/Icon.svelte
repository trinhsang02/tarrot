<script lang="ts">
  import { icon as faIcon, type IconDefinition } from "@fortawesome/fontawesome-svg-core";

  export let icon: IconDefinition;
  export let size = 24;

  $: svgHtml = faIcon(icon).html.join("");
</script>

<span
  aria-hidden="true"
  style={`display:inline-flex;width:${size}px;height:${size}px;line-height:1;align-items:center;justify-content:center;`}
>
  {@html svgHtml}
</span>