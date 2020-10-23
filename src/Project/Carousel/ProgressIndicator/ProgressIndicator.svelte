<script>
  export let mediaeCount
  export let currentIndex
  export let jumpTo

  $: dots = [...Array(mediaeCount).keys()]
</script>

<div class='progress-indicator'>
  {#each dots as dot, i}
    <svg 
      viewBox="0 0 20 20"
      on:click={() => jumpTo(i)} 
      class:active="{i == currentIndex}">
      <circle cx="10" cy="10" r="8" />
    </svg>
  {/each}
</div>

<style>
  .progress-indicator {
    display:         flex;
    flex-direction:  row;
    align-items:     center;
    justify-content: center;
    margin: var(--large-spacing);
  }
  
  svg {
    cursor: pointer;
    transition: 0.2s ease-in;
    height: var(--tiny-spacing);
    margin: 5px;
  }

  svg:hover {
    height: calc(var(--tiny-spacing) + 2px);
  }

  .active {
    cursor: auto;
    height: calc(var(--tiny-spacing) + 2px);
  }

  circle {
    fill:   var(--black);
    stroke: var(--black);
    stroke-width: 4;
    transition: 0.2s ease-in;
  }

  circle:hover {
    fill: var(--yellow);
    stroke: var(--yellow);
  }

  .active circle {
    fill: none;
  }
  
  .active circle:hover {
    stroke: var(--black);
  }
</style>