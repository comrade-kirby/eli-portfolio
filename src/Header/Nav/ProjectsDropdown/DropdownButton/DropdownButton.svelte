<script>
  export let toggleOpen
  export let open
</script>

<button class='dropdown-button' on:click={toggleOpen}>
  PROJECTS
  {#if open}
    <i class="material-icons">keyboard_arrow_up</i>
  {:else}
    <i class="material-icons">keyboard_arrow_down</i>
  {/if}
</button>

<style>
  .dropdown-button {
    display: flex;
    align-items: center;
    border: none;
    color: var(--black);
    background: transparent;
    font-size: var(--medium);
    font-weight: 600;
    padding: var(--medium);
    cursor: pointer;
  }

  i {
    margin-left: var(--tiny);
  }

  @media screen and (max-width: 600px) {
    .dropdown-button {
      font-size: var(--tiny);
      padding: var(--tiny);
    }
  }
</style>