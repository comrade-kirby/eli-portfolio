<script>
  import { onMount } from 'svelte'

  import LoadingSpinner from './LoadingSpinner.svelte'

  export let src
  export let alt


  let loaded = false
  let display = false

  const isImageLoaded = () => {
    if (loaded) { display = true }
  }
  
  const svgId = Math.floor(Math.random() * Math.floor(100000))
  const imgId = Math.floor(Math.random() * Math.floor(100000))

  onMount(() => {
    setInterval(() => {
      isImageLoaded()
    }, 1000);
  })
</script>

<div  class='image'>
  <img 
    id={imgId} 
    src={src} 
    alt={alt}
    class:display
    on:load={() => loaded = true}
    />
  {#if !display}
    <LoadingSpinner />
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

  .display {
    display: unset;
    animation: fade 0.4s;
  }

  @keyframes fade {
    from {
      opacity: 0;
    }

    to {
      opacity: 1;
    }
  }
</style>