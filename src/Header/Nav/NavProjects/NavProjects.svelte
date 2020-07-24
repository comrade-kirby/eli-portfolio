<script>
  import NavProjectsList from './NavProjectsList/NavProjectsList.svelte'
  
  export let projects

  let height
  let open = false

  const closeList = () => open = false
</script>

<div class='project-button' bind:clientHeight={height}>
  <button on:click={() => open = !open}>
    PROJECTS
    {#if open}
      <i class="material-icons">keyboard_arrow_up</i>
    {:else}
      <i class="material-icons">keyboard_arrow_down</i>
    {/if}
  </button>
  {#if open}
    <NavProjectsList 
      projects={projects} 
      buttonHeight={height} 
      closeList={closeList} />
  {/if}
</div>

<style>
 button {
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

  .project-button {
    background: transparent;
    transition: background 0.3s ease-in-out;
  }

  .project-button:hover {
    background: var(--translucent-grey);
  }

  @media screen and (max-width: 600px) {
    button {
      font-size: var(--tiny);
      padding: var(--tiny);
    }
  }
</style>