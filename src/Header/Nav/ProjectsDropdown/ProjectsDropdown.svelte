<script>
  import DropdownButton from './DropdownButton/DropdownButton.svelte'
  import DropdownList from './DropdownList/DropdownList.svelte'
  
  export let projects

  let height
  let open = false

  const toggleOpen = () => open = !open
  const openList = () => open = true
  const closeList = () => open = false
</script>

<div 
  class='projects-dropdown' 
  bind:clientHeight={height}
  on:mouseenter={openList}
  on:mouseleave={closeList}>
  <DropdownButton 
    open={open}
    toggleOpen={toggleOpen} />
  {#if open}
    <DropdownList 
      projects={projects} 
      buttonHeight={height} 
      closeList={closeList} />
  {/if}
</div>
{#if open}
  <div class='click-screen' on:click={closeList}>
  </div>
{/if}

<style>
  .projects-dropdown {
    background: transparent;
    transition: background 0.3s ease-in-out;
    z-index: 2;
  }

  .projects-dropdown:hover {
    background: var(--yellow-grey);
  }

  .click-screen {
    position: fixed;
    left: 0;
    top: 0;
    width: 100vw;
    height: 100vh;
    z-index: 1;
  }
</style>