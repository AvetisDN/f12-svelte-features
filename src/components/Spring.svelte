<script>
  //   import { writable } from "svelte/store";
  import { spring } from "svelte/motion";

  const progress = spring(
    { value: 0 },
    {
      stiffness: 0.25,
      damping: 0.25,
    }
  );
</script>

<div>
  <hr />
  <hr />
  <h3>Spring</h3>
  <hr />
  <progress value={$progress.value} />
  <button on:click={() => progress.set({ value: 0 })}>0%</button>
  <button on:click={() => progress.set({ value: 0.25 })}>25%</button>
  <button on:click={() => progress.set({ value: 0.5 })}>50%</button>
  <button on:click={() => progress.set({ value: 0.75 })}>75%</button>
  <button on:click={() => progress.set({ value: 1 })}>100%</button>
</div>

<style>
  progress {
    display: block;
    margin-bottom: 1rem;
    width: 500px;
    height: 50px;
  }
</style>
