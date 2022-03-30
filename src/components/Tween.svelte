<script>
  //   import { writable } from "svelte/store";
  import { tweened } from "svelte/motion";
  import { backIn, backOut, cubicInOut, elasticOut } from "svelte/easing";

  const progress = tweened(0, {
    duration: 300,
    easing: elasticOut,
  });
</script>

<div>
  <h3>Tween</h3>
  <hr />
  <progress value={$progress} />
  <button on:click={() => progress.set(0)}>0%</button>
  <button on:click={() => progress.set(0.25)}>25%</button>
  <button on:click={() => progress.set(0.5)}>50%</button>
  <button on:click={() => progress.set(0.75)}>75%</button>
  <button on:click={() => progress.set(1)}>100%</button>
</div>

<style>
  progress {
    display: block;
    margin-bottom: 1rem;
    width: 500px;
    height: 50px;
  }
</style>
