<script>
  export let currentMedia
</script>

<div class='carousel-content' >
  <img class='carousel-image' src={currentMedia.previous.url}  alt={currentMedia.previous.altText}/>
  <img class='carousel-image' src={currentMedia.url}  alt={currentMedia.altText}/>
  <img class='carousel-image' src={currentMedia.next.url}  alt={currentMedia.next.altText}/>
</div>

<style>
  .carousel-content {
    display:         flex;
    flex-direction:  row;
    justify-content: center;
    width:  50vh;
    height: 50vh;
    overflow: hidden;
  }

  img {
    min-width:  50vh;
    min-height: 50vh;
    object-fit: contain;
  }

  @media screen and (max-width: 600px) {
		.carousel-content {
      width:  80vw;
      height: 80vw;
    }

    img {
      min-width:  80vw;
      min-height: 80vw;
    }
	}
</style>