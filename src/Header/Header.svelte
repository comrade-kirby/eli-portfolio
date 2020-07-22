<script>
  export let projects

  import Logo from './Logo/Logo.svelte'
  import Nav from './Nav/Nav.svelte'

</script>

<header>
  <Logo />
  <Nav projects={projects} />
</header>

<style>
  header {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
</style>