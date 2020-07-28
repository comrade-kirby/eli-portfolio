<script>
  export let mediaeCount
  export let currentIndex
  export let jumpTo

  const dots = [...Array(mediaeCount).keys()]
</script>

<div class='progress-indicator'>
  {#each dots as dot, i}
    <svg 
      viewBox="0 0 20 20"
      on:click={() => jumpTo(i)} >
      <circle 
        cx="10" cy="10" r="8" 
        class:active="{i == currentIndex}" />
    </svg>
  {/each}
</div>

<style>
  .progress-indicator {
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin: var(--tiny);
  }
  
  svg {
    height: 10px;
    margin: 3px;
    cursor: pointer;
  }

  circle {
    stroke: var(--grey);
    stroke-width: 2;
    fill: none;
  }

  .active {
    fill: var(--grey);
  }
</style>