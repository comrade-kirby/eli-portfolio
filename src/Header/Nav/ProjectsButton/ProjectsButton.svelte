<script>
  let height
  let projects = ['project 1', 'project 2', 'project 3']
  let open = false
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
    <div class='project-links' style='--parent-height:{height}px'>
      {#each projects as project}
        <a 
          href='/projects/{project}'
          on:click={() => open = false}>
          {project}
        </a>
      {/each}
    </div>
{/if}
</div>

<style>
 button {
    display: flex;
    border: none;
    background: transparent;
    font-size: var(--medium);
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
    background: whitesmoke;
  }

  .project-links {
    position: absolute;
    top: var(--parent-height);
    display: flex;
    flex-direction: column;
    width: 100%;
    z-index: 1;
  }

  a {
    color: black;
    text-decoration: none;
    font-size: var(--small);
    padding: var(--small) var(--medium);
    transition: background 0.3s ease-in-out;
  }

  a:hover {
    background: whitesmoke;
  }
</style>