<script>
  export let media
</script>

<img src={media.url}  alt={media.altText}/>

<style>
  img {
    min-height: 50vh;
    min-width: 50vh;
    object-fit: contain;
  }
</style>