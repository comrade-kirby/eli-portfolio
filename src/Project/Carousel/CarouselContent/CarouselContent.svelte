<script>
  export let currentMedia
</script>

<div class='carousel-content' >
  <img src={currentMedia.previous.url}  alt={currentMedia.previous.altText}/>
  <img src={currentMedia.url}  alt={currentMedia.altText}/>
  <img src={currentMedia.next.url}  alt={currentMedia.next.altText}/>
</div>

<style>
  .carousel-content {
    display: flex;
    flex-direction: row;
    height: 50vh;
    width: 50vh;
    justify-content: center;
    overflow: hidden;
  }

  img {
    min-height: 50vh;
    min-width: 50vh;
    object-fit: contain;
  }

  @media screen and (max-width: 600px) {
		.carousel-content {
      height: 80vw;
      width: 80vw;
    }

    img {
      min-height: 80vw;
      min-width: 80vw;
    }
	}
</style>