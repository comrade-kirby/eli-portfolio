<script>
  export let slide
  export let direction
  
  const icon = direction == 'previous' 
    ? 'keyboard_arrow_left'
    : 'keyboard_arrow_right'
</script>

<button 
  class='button'
  on:click={() => slide(direction)}>
  <i class="material-icons">{icon}</i>
</button>

<style>
  .button {
    min-height: 100%;
    background: transparent;
    border: none;
    cursor: pointer;
  }

  i { 
    font-size: var(--gargantuan);
    margin: calc(-1 * var(--tiny));
    transition: color 0.2s ease-in;
  }

  .button:hover i {
    color: var(--red);
  }

  @media screen and (max-width: 600px) {
    i {
      font-size: var(--huge);
    }
	}
</style>