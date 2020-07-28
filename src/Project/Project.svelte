<script>
  import Carousel from './Carousel/Carousel.svelte'
  import { projects } from '../stores.js'

  export let projectKey

  let project

  $: project = $projects.find( project => project.key == projectKey)
</script>

{#if project}
  <section class='project'>
    <h1 class='project-name'>{project.name}</h1>
    <Carousel mediae={project.projectMediae}/>
    <div class='project-description'>
      {#each project.projectCopy as copy}
        <p>{copy}</p>
      {/each}
    </div>
  </section>
{/if}

<style>
  .project {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-end;
  }

  .project-description {
    max-width: 1000px;
  }
</style>