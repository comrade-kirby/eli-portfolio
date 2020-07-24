<script>
  export let projects

  import ProjectsList from './ProjectsList/ProjectsList.svelte'
</script>

<nav>
  <a class='nav-button' href="/about">ABOUT</a>
  <a class='nav-button' href="/contact">CONTACT</a>
  <ProjectsList projects={projects} />
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
    color: var(--black);
    text-decoration: none;
    padding: var(--medium);
    cursor: pointer;
    background: transparent;
    font-size: var(--medium);
    font-weight: 600;
    transition: background 0.3s ease-in-out;
  }

  .nav-button:hover {
    background: whitesmoke;
  }

  @media screen and (max-width: 600px) {
    .nav-button {
      font-size: var(--tiny);
      padding: var(--tiny);
    }
  }
</style>