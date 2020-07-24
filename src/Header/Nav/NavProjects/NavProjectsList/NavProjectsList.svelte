<script>
  export let projects
  export let buttonHeight
  export let closeList
</script>

<ul class='project-links' style='--parent-height:{buttonHeight}px'>
  {#each projects as project}
    <a 
      href='/projects/{project.key}'
      on:click={closeList}>
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
    color: var(--black);
    background-color: var(--translucent-white);
    text-decoration: none;
    font-size: var(--small);
    padding: var(--tiny) var(--medium);
    transition: background 0.3s ease-in-out;
  }

  a:hover {
    background: var(--translucent-grey);
  }

   @media screen and (max-width: 600px) {
    a {
      font-size: var(--tiny);
      padding: var(--tiny) var(--small);
    }
  }
</style>