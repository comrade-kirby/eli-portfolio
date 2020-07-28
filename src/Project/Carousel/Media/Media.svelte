<script>
  export let media
</script>

<img src={media.url} alt={media.altText}/>

<style>
  img {
    min-height: 50vw;
    min-width: 50vw;
    object-fit: contain;
  }
</style>