<script>
  export let src
  export let alt

  let loaded = false

  const svgId = Math.floor(Math.random() * Math.floor(100000))
  const imgId = Math.floor(Math.random() * Math.floor(100000))
</script>

<div  class='image'>
  <img 
    id={imgId} 
    src={src} 
    alt={alt}
    class:loaded
    on:load={() => loaded = true}
    />
  {#if !loaded}
    <svg 
      id={svgId}
      class='visible'
      viewBox="0 0 100 100" 
      xmlns="http://www.w3.org/2000/svg" >
      <circle cx="50" cy="50" r="40" />
    </svg>
  {/if}
</div>

<style>
  .image {
    position: relative;
    height: 100%;
    width: 100%;
  }
  
  img {
    display: none;
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  svg {
    z-index: 1;
    stroke: red;
    fill: grey;
    background-color: var(--white);
  }

  .loaded {
    display: unset;
  }
</style>