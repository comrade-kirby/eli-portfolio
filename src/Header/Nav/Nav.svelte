<script>
  import ProjectsButton from './ProjectsButton/ProjectsButton.svelte'
</script>

<nav>
  <a class='nav-button' href="/about">ABOUT</a>
  <a class='nav-button' href="/contact">CONTACT</a>
  <ProjectsButton />
</nav>

<style>
  nav {
    display: flex;
    flex-direction: row;
    align-self: flex-start;
  }

  .nav-button {
    position: relative;
    color: black;
    text-decoration: none;
    padding: var(--medium);
    cursor: pointer;
    background: transparent;
    font-size: var(--medium);
    transition: background 0.3s ease-in-out;
  }

  .nav-button:hover {
    background: whitesmoke;
  }
</style>