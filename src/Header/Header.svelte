<script>
  import Logo from './Logo/Logo.svelte'
  import Nav from './Nav/Nav.svelte'

</script>

<header>
  <Logo />
  <Nav />
</header>

<style>
  header {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
  }
</style>