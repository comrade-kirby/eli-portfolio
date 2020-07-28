<script>
  import { onMount } from 'svelte'
	import page from 'page'

	import Header from './Header/Header.svelte'
	import Home from './Home/Home.svelte'
	import About from './About/About.svelte'
	import Contact from './Contact/Contact.svelte'
	import Project from './Project/Project.svelte'
	import { projects } from './stores.js'

	let projectKey
	let component = Home

	const getProjects = async () => {
		const response = await fetch('/projects.json')
		const json = await response.json()
		return Object.keys(json).map(key => Object.assign(json[key], {key}))
	} 

	page('', () => component = Home)
	page('/about', () => component = About)
	page('/contact', () => component = Contact)
	page('/projects/:project', (ctx) => {
	component = Project
	projectKey = ctx.params.project
	})
	page('*', '')
	page.start()

	onMount( async () => {
		projects.set(await getProjects())
  })
</script>

{#if projects}
	<Header />
	<main>
		<svelte:component 
			this={component} 
			projectKey={projectKey} />
	</main>
{/if}

<style>
	:global(body) {
		--tiny: 0.75rem;
		--small: 1rem;
		--medium: 1.25rem;
		--large: 2rem;
		--huge: 3rem;
		--gargantuan: 5rem;

		--translucent-white: hsla(0, 0%, 100%, 90%);
		--translucent-grey: hsla(0, 0%, 96%, 90%);
		--black: hsla(0, 0%, 10%, 100%);
		--grey: hsla(0, 0%, 50%, 100%);
	}

	main {
		margin-right: calc(2 * var(--huge));
    margin-bottom: calc(2 * var(--huge));
    margin-left: calc(150px + (2 * var(--medium)));
	}

	:global(button) {
		outline: none;
	}

	:global(h1) {
		font-size: var(--huge);
    margin-top: calc(-1 * var(--huge));
    margin-bottom: var(--medium);
	}

	:global(p) {
		font-size: var(--medium);
		line-height: var(--large);
		margin-bottom: var(--small);
	}

	@media screen and (max-width: 1400px) {
		main {
			margin-right: var(--huge);
			margin-bottom: var(--huge);
		}
	}

	@media screen and (max-width: 1000px) {
		main {
			margin: var(--medium);
		}
	}

	@media screen and (max-width: 600px) {
		:global(h1) {
			font-size: var(--large);
		}

		:global(p) {
			font-size: var(--small);
		}
	}
</style>