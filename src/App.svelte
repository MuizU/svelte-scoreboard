<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";
  let players = [
    {
      name: "John Doe",
      points: 53,
    },
    {
      name: "Sam Smith",
      points: 45,
    },
    {
      name: "Sara Wilson",
      points: 34,
    },
  ];
  const addPlayer = (e) => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };
  const deletePlayer = (e) => {
    const { idx: fifty } = players;
    players = players.filter((p, idx) => idx !== e.detail);
  };
</script>

<Navbar />

<div class="container">
  <AddPlayer on:addplayer={addPlayer} />
  {#if players.length === 0}
    <p>No Players</p>
  {:else}
    {#each players as player, index}
      <Player
        name={player.name}
        points={player.points}
        {index}
        on:deletePlayer={deletePlayer}
      />
    {/each}
  {/if}
</div>

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
