<script>
  import Carousel from './Carousel/Carousel.svelte'
  import { projects } from '../stores.js'

  export let projectKey

  let project

  $: project = $projects.find( project => project.key == projectKey)
</script>

{#if project}
  <section class='project'>
    <h1>{project.name}</h1>
    <Carousel mediae={project.projectMediae}/>
    {#each project.projectCopy as copy}
      <p>{copy}</p>
    {/each}
  </section>
{/if}

<style>
  .project {
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
    align-items: flex-end;
  }
</style>