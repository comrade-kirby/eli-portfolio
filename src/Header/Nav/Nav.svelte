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
    display: flex;
    flex-direction: row;
    align-items: center;
    align-self: flex-start;
    margin-right: var(--huge);
  }

  .nav-button {
    position: relative;
    padding: var(--medium);
    background: transparent;
    font-size: var(--medium);
    font-weight: 700;
    z-index: 1;
  }

  @media screen and (max-width: 1400px) {
    nav {
      margin-right: var(--tiny);
    }
  }

  @media screen and (max-width: 600px) {

    nav {
      margin-right: unset;
    }

    .nav-button {
      font-size: var(--tiny);
      padding: var(--tiny);
    }
  }
</style>