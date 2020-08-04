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

		--black: rgb(45, 43, 59);
		--white: rgb(255, 253, 243);
		--yellow: rgb(235, 200, 0);
		--yellow-grey: rgb(250, 248, 240);
		--translucent-white: hsla(50, 100%, 98%, 90%);

		max-width: 1200px;
		margin: auto;
		background-color: var(--white);
	}

	:global(*) {
		padding: 0;
		margin: 0;
		font-family: 'Arial', sans-serif;
		color: var(--black);
	}

	:global(a) {
		cursor: pointer;
    text-decoration: none;
    transition: color 0.2s ease-in;
	}

	:global(a:hover) {
		color: var(--yellow);
	}

	main {
		margin-right: calc(2 * var(--gargantuan));
    margin-bottom: calc(2 * var(--gargantuan));
    margin-left: calc(150px + (2 * var(--medium)));
	}

	:global(button) {
		outline: none;
	}

	:global(h1) {
		font-size: var(--large);
    margin-bottom: var(--huge);
		font-weight: 700;
	}

	:global(p) {
		font-size: var(--medium);
		line-height: var(--large);
		margin-bottom: var(--large);
		text-align: justify;
		font-weight: 400;
	}

	@media screen and (max-width: 1400px) {
		main {
			margin-right: var(--gargantuan);
			margin-bottom: var(--gargantuan);
		}
	}

	@media screen and (max-width: 1000px) {
		main {
			margin: var(--medium);
			margin-bottom: var(--huge);
		}
	}

	@media screen and (max-width: 600px) {
		

		:global(h1) {
			font-size: var(--medium);
			/* margin-top: unset; */
		}

		:global(p) {
			font-size: var(--small);
		}
	}
</style>