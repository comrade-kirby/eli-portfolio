<script>
  export let project
  
  let hover = false
</script>

<a 
  class='project'
  href='/projects/{project.key}'
  on:mouseenter={ () => hover = true }
  on:mouseleave={ () => hover = false }>
  <img class='primary' class:hover src={project.homePrimary} />
  <img class='secondary' class:hover src={project.homeSecondary} />
</a>

<style>
 .project {
    width: 100%;
    cursor: pointer;
    position: relative;
  }

  .project::before {
    content: "";
    display: inline-block;
    padding-bottom: 100%;
  }

  img {
    height: 100%;
    width: 100%;
    object-fit: contain;
    position: absolute;
    transition: opacity 0.2s ease-out;
  }

  .secondary {
    z-index: 0;
    opacity: 0;
  }

  .primary.hover {
    opacity: 0;
  }

  .secondary.hover {
    opacity: 1;
  }
</style>