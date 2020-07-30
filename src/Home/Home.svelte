<script>
  import ProjectIcon from './ProjectIcon/ProjectIcon.svelte'
  
  import { projects } from '../stores.js'
</script>

<section class='home'>
  {#each $projects as project}
    <ProjectIcon project={project} />
  {/each}
</section>

<style>
  .home {
    display: grid;
    grid-gap: var(--huge-spacing);
    grid-template-columns: repeat(3, 1fr);
  }

  @media screen and (max-width: 1400px) {
    .home {
      grid-gap: var(--small-spacing)
    }
  }

  @media screen and (max-width: 1000px) {
    .home {
      grid-gap: var(--gargantuan-spacing);
      grid-template-columns: repeat(2, 1fr);
    }
  }
  
  @media screen and (max-width: 600px) {
    .home {
      grid-gap: var(--medium-spacing);
    }
  }
</style>