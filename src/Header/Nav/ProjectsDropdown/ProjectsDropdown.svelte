<script>
  import DropdownButton from './DropdownButton/DropdownButton.svelte'
  import DropdownList from './DropdownList/DropdownList.svelte'
  
  export let projects

  let height
  let open = false

  const toggleOpen = () => open = !open
</script>

<div 
  class='projects-dropdown' 
  bind:clientHeight={height}
  on:mouseenter={toggleOpen}
  on:mouseleave={toggleOpen}>
  <DropdownButton 
    open={open}
    toggleOpen={toggleOpen} />
  {#if open}
    <DropdownList 
      projects={projects} 
      buttonHeight={height} 
      toggleOpen={toggleOpen} />
  {/if}
</div>

<style>
  .projects-dropdown {
    background: transparent;
    transition: background 0.3s ease-in-out;
  }

  .projects-dropdown:hover {
    background: var(--translucent-grey);
  }
</style>