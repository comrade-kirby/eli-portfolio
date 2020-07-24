<script>
  import ProjectIcon from './ProjectIcon/ProjectIcon.svelte'
  
  export let projects
</script>

<div class='projects'>
  {#each projects as project}
    <ProjectIcon project={project} />
  {/each}
</div>

<style>
  .projects {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    margin-right: calc(2 * var(--huge));
    margin-bottom: calc(2 * var(--huge));
    margin-left: calc(150px + (2 * var(--medium)));
    grid-gap: var(--huge);
  }

  @media screen and (max-width: 1400px) {
    .projects {
      margin-right: var(--huge);
      margin-bottom: var(--huge);
      grid-gap: var(--large);
    }
  }

  @media screen and (max-width: 1000px) {
    .projects {
      grid-template-columns: repeat(2, 1fr);
      margin: var(--medium);
    }
  }
  
  @media screen and (max-width: 600px) {
    .projects {
      grid-gap: var(--medium);
    }
  }
</style>