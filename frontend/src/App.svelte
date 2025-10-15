<script lang="ts">
  let hello = $state<string>("");

  $effect(() => {
    (async () => {
      const response = await fetch("/hello");

      console.log(response);

      if (!response.ok) {
        throw new Error("Failed to fetch");
      }

      const data = await response.text();

      hello = data;
    })();
  });
</script>

<main>
  <div style="padding: 24px">
    <h1>Ripress + Svelte minimal demo</h1>
    <div>
      <h2>/hello</h2>
      <pre>{hello ?? "Loading..."}</pre>
    </div>
  </div>
</main>
