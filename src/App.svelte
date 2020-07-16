<script>
	import page from 'page'

	import Header from './Header/Header.svelte'
	import Home from './Home/Home.svelte'
	import About from './About/About.svelte'
	import Contact from './Contact/Contact.svelte'
	import Project from './Project/Project.svelte'

	let component = Home

	page('', () => component = Home)
	page('/about', () => component = About)
	page('/contact', () => component = Contact)
	page('/project/:project', () => component = Project)
	page('*', '')
	page.start()
</script>

<main>
	<Header />
	<svelte:component this={component}/>
</main>

<style>
</style>