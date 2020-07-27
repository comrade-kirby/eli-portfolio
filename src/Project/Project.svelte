<script>
  import { projects } from '../stores.js'

  export let projectKey

  let project

  $: project = $projects.find( project => project.key == projectKey)
</script>

{#if project}
  <h1>{project.name}</h1>
  {#each project.project_copy as copy}
    <p>{copy}</p>
  {/each}
{/if}