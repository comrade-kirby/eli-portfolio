<script>
  import { onMount } from 'svelte'
	import page from 'page'

	import Header from './Header/Header.svelte'
	import Home from './Home/Home.svelte'
	import About from './About/About.svelte'
	import Contact from './Contact/Contact.svelte'
	import Project from './Project/Project.svelte'

	let projects
	let component = Home

	const getProjects = async () => {
    const response = await fetch('projects.json')
    const json = await response.json()
    return Object.keys(json).map(key => json[key])
	} 
	
	page('', () => component = Home)
	page('/about', () => component = About)
	page('/contact', () => component = Contact)
	page('/projects/:project', () => component = Project)
	page('*', '')
	page.start()

	onMount(async () => {
		projects = await getProjects()
  })
</script>

<main>
	{#if projects}
		<Header projects={projects} />
		<svelte:component this={component} projects={projects} />
	{/if}
</main>

<style>
	main {
		--tiny: 0.75rem;
		--small: 1rem;
		--medium: 1.25rem;
		--large: 1.5rem;
		--huge: 3rem;

		--translucent-white: hsla(0, 0%, 100%, 90%);
		--translucent-grey: hsla(0, 0%, 96%, 90%);
		--black: hsla(0, 0%, 10%, 100%);
	}
</style>