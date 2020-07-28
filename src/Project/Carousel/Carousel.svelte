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
    const translate = direction == 'previous' ? 400 : -400
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
    class='button previous'
    on:click={() => slide('previous')}>
    <i class="material-icons">keyboard_arrow_left</i>
  </button>  
  <div class='mediae-container'>
    <Media media={currentMedia.previous} />
    <Media media={currentMedia} />
    <Media media={currentMedia.next} />
  </div>
  <button class='button next'
    on:click={() => slide('next')}>
    <i class="material-icons">keyboard_arrow_right</i>
  </button>
</div>

<style>
  .carousel {
    position: relative;
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
    position: absolute;
    top: 0;
    height: 100%;
    background: white;
    border: none;
    z-index: 1;
    cursor: pointer;
  }

  .previous {
    left: 0;
  }

  .next {
    right: 0;
  }

  i { 
    font-size: var(--huge);
  }
</style>