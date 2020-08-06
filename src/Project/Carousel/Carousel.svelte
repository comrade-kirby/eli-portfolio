<script>
  import anime from 'animejs/lib/anime.es.js'

  import CarouselContent from './CarouselContent/CarouselContent.svelte'
  import CarouselButton from './CarouselButton/CarouselButton.svelte'
  import ProgressIndicator from './ProgressIndicator/ProgressIndicator.svelte'
  import SwipeDetect from './SwipeDetect/SwipeDetect.svelte'

  export let mediae

  let currentMedia, height, hover
  
  const linkMediae = (mediae) => {
    if (mediae.length) {
      
      mediae.forEach((media, i) => {
        
        media.index = i
        
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
    const targets = '.carousel-image'

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

  const jumpTo = (index) => currentMedia = mediae[index]

  $: linkMediae(mediae)
</script>


{#if mediae.length}
  <div class='carousel-container'
    on:mouseenter={() => hover = true}
    on:mouseleave={() => hover = false}>
    <div class='carousel' bind:clientHeight={height}>
      <CarouselButton 
        slide={slide}
        hover={hover}
        direction='previous' />  
      <CarouselContent currentMedia={currentMedia} />
      <CarouselButton 
        slide={slide}
        hover={hover}
        direction='next' />  
    </div>
    <ProgressIndicator 
      mediaeCount={mediae.length} 
      currentIndex={currentMedia.index}
      jumpTo={jumpTo} />
    <SwipeDetect slide={slide} />
  </div>
{/if}

<style>
  .carousel-container {
    position: relative;
    display:         flex;
    flex-direction:  column;
    justify-content: center;
    margin-bottom: var(--large-spacing);
  }

  .carousel {
    position:        relative;
    display:         flex;
    flex-direction:  row;
    justify-content: flex-end;
    width: 100%;
  }

  @media screen and (max-width: 600px) {
    .carousel {
      justify-content: space-around;
    }
	}
</style>