<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let name;
  export let points;
  export let index;
  let showControls = false;

  const addPoint = () => points++;
  const removePoint = () => points--;
  const toggleControls = () => (showControls = !showControls);
  const deletePlayer = () => {
    dispatch("deletePlayer", index);
  };
</script>

<main>
  <div class="card">
    <h1>
      {name}
      <button class="btn btn-sm" on:click={toggleControls}>
        {#if showControls}-{:else}+{/if}
      </button>
      <button class="btn btn-sm" on:click={deletePlayer}>X</button>
    </h1>
    <h3>Points: {points}</h3>
    {#if showControls}
      <button class="btn" on:click={addPoint}>+1</button>
      <button class="btn btn-dark" on:click={removePoint}> -1 </button>
      <input type="number" bind:value={points} />
    {/if}
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
  h3 {
    margin-bottom: 10px;
  }
</style>
