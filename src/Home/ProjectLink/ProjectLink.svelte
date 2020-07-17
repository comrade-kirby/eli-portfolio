<script>
  export let image
  
  let hover = false
</script>

<div 
  class='project'
  on:mouseenter={ () => hover = true }
  on:mouseleave={ () => hover = false }>
  <img class:hover src={image[0].download_url} />
  <img class='hover-img' src={image[1].download_url} />
</div>

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
    object-fit: cover;
    z-index: 1;
    position: absolute;
  }

  .hover-img {
    z-index: 0;
  }

  .hover {
    opacity: 0;
  }
</style>