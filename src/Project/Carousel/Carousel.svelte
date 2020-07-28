<script>
  import anime from 'animejs/lib/anime.es.js'

  export let mediae

  let currentMedia
  let linkedMediae = []
  
  const linkMediae = (mediae) => {
    mediae.forEach((media, i) => {
      const newNode = {
        url: media
      }
      
      linkedMediae.push(newNode)

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

    anime({
      targets: 'img',
      translateX: translate,
      duration: 300,
      easing: 'easeInOutCubic',
      complete: () => {
        anime({
          targets: 'img',
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
  <div class='media-container'>
    <img src={currentMedia.previous.url} />
    <img src={currentMedia.url} />
    <img src={currentMedia.next.url} />
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

  .media-container {
    display: flex;
    flex-direction: row;
    height: 400px;
    width: 400px;
    justify-content: center;
    overflow: hidden;
  }

  .button {
    position: absolute;
    top: 0;
    height: 100%;
    background: transparent;
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

  img {
    height: 400px;
    min-width: 400px;
    object-fit: contain;
  }

  i { 
    font-size: var(--huge);
  }
</style>