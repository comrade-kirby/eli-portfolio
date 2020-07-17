<script>
  export let image
</script>

<div class='project'>
  <img src={image[0].download_url} />
</div>

<style>
 .project {
    width: 100%;
    cursor: pointer;
  }

  .project::before {
    content: "";
    display: inline-block;
    padding-bottom: 100%;
  }

  img {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
</style>