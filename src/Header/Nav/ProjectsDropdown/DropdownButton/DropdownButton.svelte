<script>
  export let open
  export let toggleOpen
  export let disableHover

  let rotation = 180

  const rand180 = (open) => rotation = open ? -rotation : rotation

  $: rand180(open)
</script>

<button 
  class:open
  class='dropdown-button'
  on:touchstart={disableHover}
  on:click={toggleOpen}
  style='--degrees:{rotation}deg'>
  PROJECTS
  <i class="material-icons">keyboard_arrow_up</i>
</button>

<style>
  .dropdown-button {
    display:     flex;
    align-items: center;
    border: none;
    color: var(--black);
    background: transparent;
    font-size: var(--small-font);
    font-weight: 700;
    color:       var(--black);
    cursor: pointer;
    border: none;
    background: transparent;
    padding: var(--medium-spacing);
  }

  i {
    transition: 0.2s ease-in;
    margin-left: var(--tiny-spacing);
  }

  .open i {
    transform: rotateZ(var(--degrees));
  }

  @media screen and (max-width: 600px) {
    .dropdown-button {
      font-size: var(--tiny-font);
      padding: var(--tiny-spacing);
    }
  }
</style>