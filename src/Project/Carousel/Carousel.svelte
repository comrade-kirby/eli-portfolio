<script>
  import anime from 'animejs/lib/anime.es.js'

  import Media from './Media/Media.svelte'

  export let mediae

  let currentMedia, height
  let linkedMediae = []
  
  const linkMediae = (mediae) => {
    mediae.forEach((media, i) => {
      linkedMediae.push(media)

      if (linkedMediae[i - 1]) { 
        linkedMediae[i].previous = linkedMediae[i - 1] 
        linkedMediae[i - 1].next = linkedMediae[i]
      }
    })

    const firstNode = linkedMediae[0]
    const lastNode = linkedMediae[linkedMediae.length - 1]
    firstNode.previous = lastNode
    lastNode.next = firstNode

    currentMedia = firstNode
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

<div class='carousel'>
  <button 
    class='button'
    on:click={() => slide('previous')}>
    <i class="material-icons">keyboard_arrow_left</i>
  </button>  
  <div class='mediae-container' bind:clientHeight={height}>
    <Media media={currentMedia.previous} />
    <Media media={currentMedia} />
    <Media media={currentMedia.next} />
  </div>
  <button class='button'
    on:click={() => slide('next')}>
    <i class="material-icons">keyboard_arrow_right</i>
  </button>
</div>

<style>
  .carousel {
    position: relative;
    display: flex;
    flex-direction: row;
  }

  .mediae-container {
    display: flex;
    flex-direction: row;
    height: 50vh;
    width: 50vh;
    justify-content: center;
    overflow: hidden;
  }

  .button {
    min-height: 100%;
    background: white;
    border: none;
    cursor: pointer;
  }

  i { 
    font-size: var(--huge);
  }
</style>