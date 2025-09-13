<script lang="ts">

let  hello = $state<any>(null);

$effect(() => {
  (async () => {
    const response = await fetch("/hello");

    if (!response.ok) {
      throw new Error("Failed to fetch");
    }

    const data = await response.json();

    hello = data;
  })();
});
</script>

<main>
  <div style="padding: 24px">
    <h1>Ripress + Svelte minimal demo</h1>
    <div>
      <h2>/hello</h2>
      <pre>{hello ? JSON.stringify(hello, null, 2) : "Loading..."}</pre>
    </div>
  </div>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>