<script>
  import { onMount } from 'svelte'

  import ProjectLink from './ProjectLink/ProjectLink.svelte'
  
  let images

  const groupImages = (data) => {
    let images = []
    data.forEach((item, i) => {
      if (i % 2 == 0 ) {
        images.push([item])
      } else {
        images[images.length - 1].push(item)
      }
    })
   return images
  }

  const getImages = () => {
    fetch('https://picsum.photos/v2/list')
    .then(response => response.json())
    .then(data => images = groupImages(data))
  } 

  onMount(() => {
    getImages()
  })
</script>

<div class='projects'>
  {#if images}
    {#each images as image}
      <ProjectLink image={image} />
    {/each}
  {/if}
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
    }
  }

  @media screen and (max-width: 1000px) {
    .projects {
      grid-template-columns: repeat(2, 1fr);
      margin: var(--medium);
    }
  }
</style>