<script>
  import { onMount } from 'svelte'
  import { fade } from 'svelte/transition'
  import anime from 'animejs/lib/anime.es.js'

  export let projects
  export let buttonHeight
  export let closeList

  onMount(() => {
    anime({
      targets: '.dropdown-link',
      opacity: [0, 1],
      duration: 1000,
      delay: anime.stagger(10)
    })
  })
</script>

<ul 
  out:fade="{{duration: 200 }}"
  class='dropdown-list' 
  style='--parent-height:{buttonHeight}px'>
  {#each projects as project}
    <a 
      class='dropdown-link'
      href='/projects/{project.key}'
      on:click={closeList}>
      {project.name}
    </a>
  {/each}
</ul>

<style>
  .dropdown-list {
    display:        flex;
    flex-direction: column;
    position:       absolute;
    top: var(--parent-height);
    width: 100%;
    z-index: 2;
  }

  a {
    font-size: var(--small-font);
    background-color: var(--translucent-white);
    padding: var(--tiny-spacing) var(--medium-spacing);
    z-index: 2;
  }

   @media screen and (max-width: 600px) {
    a {
      font-size: var(--tiny-font);
      padding: var(--small-spacing) var(--small-spacing);
    }
  }
</style>