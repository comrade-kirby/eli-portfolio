<script>
  import Image from '../../shared/Image.svelte'
  
  
  export let project
  
  let hover = false
</script>

<a 
  class='project'
  href='/projects/{project.key}'
  on:mouseenter={ () => hover = true }
  on:mouseleave={ () => hover = false }>
  <div 
    class='img-container primary'
    class:hover >
    <Image src={project.homePrimary} alt='{project.name} thumbnail' />
  </div>
  <div 
    class='img-container secondary'
    class:hover >
    <Image src={project.homeSecondary} alt='{project.name} label' />
  </div>
</a>

<style>
 .project {
    position: relative;
    display: block;
    width: 100%;
    height: 100%;
  }

  .img-container {
    transition: opacity 0.2s ease-out;
  }

  .secondary {
    position: absolute;
    top: 0;
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