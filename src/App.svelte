<script>
  import Team from "./Team.svelte";
  let redScore = 20;
  let blueScore = 20;
  $: redWon = blueScore === 0;
  $: blueWon = redScore === 0;
  $: gameOver = redWon || blueWon;
  function reset(){
    redScore = 20;
    blueScore = 20;
  }
</script>

<div class="row mt-2">
  <div class="col" >
    <h1 class="text-center">MTG Counter</h1>

  </div>
</div>
<div class="row">
<Team  {gameOver} team='Red' bind:score= {redScore}/>
<Team {gameOver} team='Blue' bind:score= {blueScore}/>
</div>
<div class="row mt-3">
  <div class="col">
    {#if blueWon}
    <h2 class="text-center text-primary">Blue won</h2>
    {:else}
    <h2 class="text-center text-danger">Red won</h2>
    {/if}
  </div>
</div>
{#if !gameOver}
<div class="row mt-3">
  <div class="col ">
    <button class="btn btn-warning w-100" on:click={reset}>Reset</button>
  </div>
  
</div>
{:else}

<div class="row mt-3">
  <div class="col">
    <button class="btn btn-success w-100" on:click={reset}>New Game</button>
  </div>
</div>
{/if}



