<script>
  import { onMount } from "svelte";
  let { children } = $props();
</script>

<svelte:head>
  <meta name="description" content="charmIT - tech help for everyone" />
</svelte:head>

{@render children()}

<style>
  :global(*, *::before, *::after) {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  :global(:root) {
    --bg: #080b0f;
    --surface: #0d1117;
    --border: rgba(255, 255, 255, 0.07);
    --accent: #00ff88;
    --accent-dim: rgba(0, 255, 136, 0.12);
    --text: #e8eaf0;
    --muted: #6b7280;
    --mono: "IBM Plex Mono", monospace;
    --sans: "IBM Plex Sans", sans-serif;
  }
  :global(body) {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-size: 16px;
    line-height: 1.7;
  }
  :global(html) {
    scroll-behavior: smooth;
  }
  :global(a) {
    color: inherit;
    text-decoration: none;
  }
</style>
