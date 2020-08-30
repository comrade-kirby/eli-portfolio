<script>
  import Image from '../../../shared/Image.svelte'
  export let currentMedia
</script>

<div class='carousel-content' >
  <div class='carousel-image'>
    <Image 
      src={currentMedia.previous.url} 
      alt={currentMedia.previous.altText} />
  </div>
  <div class='carousel-image'>
    <Image 
      src={currentMedia.url} 
      alt={currentMedia.altText}/>
  </div>
  <div class='carousel-image'>
    <Image
      src={currentMedia.next.url} 
      alt={currentMedia.next.altText}/>
  </div>
</div>

<style>
  .carousel-content {
    display:         flex;
    flex-direction:  row;
    justify-content: center;
    width:  75vh;
    height: 75vh;
    overflow: hidden;
  }

  .carousel-image {
    min-width:  75vh;
    min-height: 75vh;
  }

  @media screen and (max-width: 1000px) {
		.carousel-content {
      width:  80vw;
      height: 80vw;
    }

    .carousel-image {
      min-width:  80vw;
      min-height: 80vw;
    }
	}
</style>