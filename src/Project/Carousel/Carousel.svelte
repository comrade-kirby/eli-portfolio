<script>
  import anime from 'animejs/lib/anime.es.js'

  import CarouselContent from './CarouselContent/CarouselContent.svelte'
  import CarouselButton from './CarouselButton/CarouselButton.svelte'

  export let mediae

  let currentMedia, height
  
  const linkMediae = (mediae) => {
    if (mediae.length) {

      mediae.forEach((media, i) => {

      if (mediae[i - 1]) { 
        mediae[i].previous = mediae[i - 1] 
        mediae[i - 1].next = mediae[i]
        }
      })

      const firstNode = mediae[0]
      const lastNode = mediae[mediae.length - 1]
      firstNode.previous = lastNode
      lastNode.next = firstNode

      currentMedia = firstNode
    }
  }

  const slide = (direction) => {
    const translate = direction == 'previous' ? height : -height
    const nextMedia = direction == 'previous' 
      ? currentMedia.previous 
      : currentMedia.next
    const targets = 'img'

    anime({
      targets,
      translateX: translate,
      duration: 300,
      easing: 'easeInOutCubic',
      complete: () => {
        anime({
          targets,
          translateX: 0,
          duration: 0
        })
        currentMedia = nextMedia
      }
    });
  }

  $: linkMediae(mediae)
</script>

{#if mediae.length}
  <div class='carousel' bind:clientHeight={height}>
    <CarouselButton 
      onclick={slide}
      direction='previous' />  
    <CarouselContent currentMedia={currentMedia} />
    <CarouselButton 
      onclick={slide}
      direction='next' />  
  </div>
{/if}

<style>
  .carousel {
    position: relative;
    display: flex;
    flex-direction: row;
  }
</style>