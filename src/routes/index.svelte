<script context="module">
	import { GraphQLClient, gql, request } from 'graphql-request';
	import { variables } from '$lib/variables'

	export async function load() {
	  const graphcms = new GraphQLClient(variables.baseUrl,
	  {
	  	headers: {}
	  });

		const QUERY = gql`
	    {
	      posts {
	      	id
	        title
	        tags
	        readTime
	        image {
	        	url
	        }
	        description
	      }
	    }
	  ` 
	  const { posts } = await graphcms.request(QUERY)
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
  import CarouselCard from '$lib/CarouselCard.svelte'

	$: searchQuery = ""
	$: searchResult = posts.filter(
		post => post.title.toLowerCase().includes(searchQuery.toLowerCase())
	).reverse()
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<section>
	<Search
		light
		placeholder="Search posts" 
		bind:value={ searchQuery } 
	/>
</section>

<h1>Featured News</h1>

<div class="carousel">
	{#each posts as post}
		<CarouselCard post={post} />
	{/each}
</div>

<h1>Other News</h1>

<div class="posts">
	{#if searchResult.length}
		{#each searchResult as post}
			<PostCard post={post} />
		{/each}
	{:else}
		<p>No posts found for {searchQuery}</p>
	{/if}
</div>

<style>
	.posts {
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-gap: .5em;
		margin: 2em 0;
	}

	.carousel {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}

	h1 {
		font-size: 2em;
		font-weight: 500;
		margin: .5em 0;
		text-align: center;
		color: #023047;
	}

	section {
		z-index: 1;
		margin:  0 2em;
		display: flex;
		justify-content: center;
		align-items: center;
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
