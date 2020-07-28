<script>
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

  $: linkMediae(mediae)
</script>

<div class='carousel'>
  <button class='button left-button'>
    <i class="material-icons">keyboard_arrow_left</i>
  </button>  
  <div class='media-container'>
    <img src={currentMedia.previous.url} />
    <img src={currentMedia.url} />
    <img src={currentMedia.next.url} />
  </div>
  <button class='button right-button'>
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
  }

  .left-button {
    left: 0;
  }

  .right-button {
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