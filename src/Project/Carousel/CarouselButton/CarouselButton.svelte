<script>

  export let onclick
  export let direction
  const icon = direction == 'previous' 
    ? 'keyboard_arrow_left'
    : 'keyboard_arrow_right'
</script>

<button 
  class='button'
  on:click={() => onclick(direction)}>
  <i class="material-icons">{icon}</i>
</button>

<style>
  .button {
    min-height: 100%;
    background: white;
    border: none;
    cursor: pointer;
  }

  i { 
    font-size: var(--huge);
  }
</style>