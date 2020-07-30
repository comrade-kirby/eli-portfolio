<script>
  import Logo from './Logo/Logo.svelte'
  import Nav from './Nav/Nav.svelte'
  import { projects } from '../stores.js'
</script>

<header>
  <Logo />
  <Nav projects={$projects} />
</header>

<style>
  header {
    display:         flex;
    flex-direction:  row;
    justify-content: space-between;
  }
</style>