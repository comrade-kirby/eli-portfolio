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
    position: absolute;
    right: 0;
    cursor: pointer;
    min-height: 100%;
    border: none;
    background: transparent;
    transition: 0.2s ease-in;
    opacity: 0;
    visibility: hidden;
    z-index: 1;
  }

  .left {
    left: 0;
    right: unset;
  }
  .hover {
    visibility: visible;
    opacity: 1;
  }

  i { 
    transition: color 0.2s ease-in;
    font-size: var(--gargantuan-font);
    color: black;
    -webkit-text-stroke: 1px var(--white);
  }

  .button:hover i {
    color: var(--yellow);
  }

  @media screen and (max-width: 600px) {
    i {
      font-size: var(--huge-font);
    }
	}
</style>