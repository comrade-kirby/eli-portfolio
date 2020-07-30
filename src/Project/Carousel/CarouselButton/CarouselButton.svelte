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
    cursor: pointer;
    min-height: 100%;
    border: none;
    background: transparent;
  }

  i { 
    transition: color 0.2s ease-in;
    font-size: var(--gargantuan-font);
    margin: calc(-1 * var(--tiny-spacing));
  }

  .button:hover i {
    color: var(--red);
  }

  @media screen and (max-width: 600px) {
    i {
      font-size: var(--huge-font);
    }
	}
</style>