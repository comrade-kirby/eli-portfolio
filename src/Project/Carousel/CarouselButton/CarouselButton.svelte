<script>
  export let slide
  export let hover 
  export let direction
  
  const icon = direction == 'previous' 
    ? 'keyboard_arrow_left'
    : 'keyboard_arrow_right'
</script>

<button 
  class='button'
  class:hover
  class:left={direction == 'previous'}
  on:click={() => slide(direction)}>
  <i class="material-icons">{icon}</i>
</button>

<style>
  .button {
    cursor: pointer;
    min-height: 100%;
    border: none;
    background: transparent;
    transition: 0.2s ease-in;
    opacity: 0;
    visibility: hidden;
    z-index: 1;
    margin-right: calc(-1 * var(--medium-spacing));
  }

  .left {
    margin-left: calc(-1 * var(--medium-spacing));
    margin-right: unset;
  }

  .hover {
    visibility: visible;
    opacity: 1;
  }

  i { 
    transition: color 0.2s ease-in;
    font-size: var(--gargantuan-font);
    color: black;
  }

  .button:hover i {
    color: var(--yellow);
  }

  @media screen and (max-width: 700px) {
    .button {
      margin-right: calc(-1 * var(--small-spacing));
    }

    .left {
      margin-left: calc(-1 * var(--small-spacing));
      margin-right: unset;
    }
    
    i {
      font-size: var(--huge-font);
    }
	}
</style>