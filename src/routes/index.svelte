<script context="module">
	export async function load ({ fetch }) {
		const res = await fetch("https://jsonplaceholder.typicode.com/posts")
		const posts = await res.json()
		return {
			props: {
				posts
			}
		}
	}
</script>

<script>
	export let posts
	import 'carbon-components-svelte/css/white.css'
  import { Search } from 'carbon-components-svelte'
  import PostCard from '$lib/PostCard.svelte'

	let searchQuery = ""
	$: searchResult = posts.filter(
		post => post.title.toLowerCase().includes(searchQuery.toLowerCase()) || post.body.toLowerCase().includes(searchQuery.toLowerCase())
	).reverse()
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<h1>Featured Posts</h1>

<section>
	<Search
		light
		placeholder="Search posts" 
		bind:value={ searchQuery } 
	/>
</section>

<div class="posts">
	{#if searchResult.length}
		{#each searchResult as post}
			<PostCard post={post} }/>
		{/each}
	{:else}
		<p>No posts found for {searchQuery}</p>
	{/if}
</div>

<style>
	.posts {
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-gap: 1em;
		margin: 2em 0;
	}

	h1 {
		font-size: 2em;
		margin: .5em 0;
		text-align: center;
	}

	section {
		z-index: 1;
		margin:  0 .3em;
	}

	@media screen and (max-width:  600px) {
		.posts {
		display: grid;
		grid-template-columns: 1fr;
		grid-gap: 1em;
		margin: 2em .5em;
	}
	}
</style>
