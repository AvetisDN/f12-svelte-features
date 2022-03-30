<script>
  import { fade, slide, scale, fly } from "svelte/transition";
  let visible = false;
  let status = "idle...";
  let count = 0;
  let direction = 1;
</script>

<div class="container">
  <label class="switcher">
    <input type="checkbox" bind:checked={visible} />
    <div><div /></div>
  </label>
  <h4>
    {status}
  </h4>
  {#if visible}
    <h2
      in:fly={{ x: -200, duration: 500 }}
      out:scale={{ duration: 400 }}
      on:introstart={() => (status = "intro start")}
      on:introend={() => (status = "intro end")}
      on:outrostart={() => (status = "outro start")}
      on:outroend={() => (status = "outro end")}
    >
      Hello Beautiful People 😙
    </h2>
  {/if}
  <hr />
  <button
    on:click={() => {
      ++count;
      direction = 1;
    }}>+</button
  >
  <button
    on:click={() => {
      --count;
      direction = -1;
    }}>-</button
  >
  <div>
    Counter equals:
    {#key count}
      <span
        class="counter"
        in:fly={{ y: direction * 20, duration: 400 }}
        out:fly={{ y: direction * -20, duration: 400 }}
      >
        {count}
      </span>
    {/key}
  </div>
</div>

<style>
  .container {
    margin-top: 3rem;
  }
  h2 {
    background: #e0fff7;
    color: #1fcf95;
    padding: 1.5rem;
    border-radius: 1rem;
    border: 2px solid #1fcf95;
    display: inline-block;
  }
  .switcher {
    display: inline-block;
  }
  .switcher input {
    display: none;
  }
  .switcher > input + div {
    display: block;
    width: 4rem;
    height: 2rem;
    /* background-color: #1fcf95;
    border: 6px solid #1fcf95; */
    background-color: #adbdb8;
    border: 4px solid #adbdb8;
    border-radius: 999px;
    cursor: pointer;
    transition-property: background, border-color;
    transition-duration: 200ms;
    transition-timing-function: ease;
  }
  .switcher > input + div > div {
    width: 2rem;
    height: 2rem;
    background: #fff;
    border-radius: 50%;
    transition-property: transform;
    transition-duration: 200ms;
    transition-timing-function: ease;
  }
  .switcher > input:checked + div {
    background-color: #1fcf95;
    border: 4px solid #1fcf95;
  }
  .switcher > input:checked + div > div {
    transform: translateX(2rem);
  }
  hr {
    margin: 2rem 0;
  }
  .counter {
    display: inline-block;
    position: absolute;
    margin-left: 0.5rem;
  }
</style>
