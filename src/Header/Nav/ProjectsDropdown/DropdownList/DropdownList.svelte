<script>
  export let projects
  export let buttonHeight
  export let toggleOpen
</script>

<ul class='project-links' style='--parent-height:{buttonHeight}px'>
  {#each projects as project}
    <a 
      href='/projects/{project.key}'
      on:click={toggleOpen}>
      {project.name}
    </a>
  {/each}
</ul>

<style>
  .project-links {
    position: absolute;
    top: var(--parent-height);
    display: flex;
    flex-direction: column;
    width: 100%;
    z-index: 2;
  }

  a {
    background-color: var(--translucent-white);
    font-size: var(--small);
    padding: var(--tiny) var(--medium);
    z-index: 2;
  }

   @media screen and (max-width: 600px) {
    a {
      font-size: var(--tiny);
      padding: var(--tiny) var(--small);
    }
  }
</style>