<script>
  export let projects

  import ProjectsDropdown from './ProjectsDropdown/ProjectsDropdown.svelte'
</script>

<nav>
  <a class='nav-button' href="/about">ABOUT</a>
  <a class='nav-button' href="/contact">CONTACT</a>
  <ProjectsDropdown projects={projects} />
</nav>

<style>
  nav {
    display:        flex;
    flex-direction: row;
    align-items:    center;
    align-self: flex-start;
  }

  .nav-button {
    position: relative;
    background: transparent;
    font-size: var(--small-font);
    font-weight: 700;
    padding: var(--medium-spacing);
    background: transparent;
    z-index: 1;
  }

  @media screen and (max-width: 700px) {
    .nav-button {
      font-size: var(--tiny-font);
      padding: var(--tiny-spacing);
    }
  }
</style>