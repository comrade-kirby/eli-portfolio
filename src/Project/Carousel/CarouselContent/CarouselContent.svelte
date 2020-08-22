<script>
  import { baseUrl } from '../../../stores'
  
  export let currentMedia
</script>

<div class='carousel-content' >
  <img class='carousel-image' src={$baseUrl + currentMedia.previous.url}  alt={currentMedia.previous.altText}/>
  <img class='carousel-image' src={$baseUrl + currentMedia.url}  alt={currentMedia.altText}/>
  <img class='carousel-image' src={$baseUrl + currentMedia.next.url}  alt={currentMedia.next.altText}/>
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

  img {
    min-width:  75vh;
    min-height: 75vh;
    object-fit: contain;
  }

  @media screen and (max-width: 1000px) {
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