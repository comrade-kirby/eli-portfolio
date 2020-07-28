<script>
  export let mediae

  $: console.log(mediae)
</script>

{#each mediae as media}
  <p>{media}</p>
{/each}

<p>this is a carousel</p>