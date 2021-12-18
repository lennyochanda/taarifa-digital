<script context="module">
	import { GraphQLClient, gql, request } from 'graphql-request';
	import { variables } from '$lib/variables'
	import { page } from '$app/stores'


	export async function load({ page }) {
		const id = await page.params.id
	  const graphcms = new GraphQLClient(variables.baseUrl,
	  {
	  	headers: {}
	  });

		const QUERY = gql`
	    {
	      posts(where: {id: "${id}"}) {
	      	id
	        title
	        tags
	        readTime
	        image {
	        	url
	        }
	        description
	        authorId
	        published
	        content {
	        	html
	        }
	      }
	    }
	  ` 
	  const post = await graphcms.request(QUERY)
		return {
			props: {
				post
			}
		}
	}
	load().catch((error) => console.error(error))
</script>

<script>
	export let post
	import Time16 from 'carbon-icons-svelte/lib/Time16'
</script>

<div class="container">
	<h2>{post.posts[0].title}</h2>
	<div class="viewInfo">
		<p>Written by <a href="/authors">{post.posts[0].authorId}</a> on {post.posts[0].published}</p>
	</div>

	<p class="description">
		{post.posts[0].description[0]}
	</p>

	<div class="wrapper">
		<img src={post.posts[0].image[0].url} alt="About this post">
	</div>
	<p>{@html post.posts[0].content[0].html}</p>

	<h2>About {post.posts[0].authorId}</h2>

	<p>by <a sveltekit:prefetch href={`/authors/`}>{ post.posts[0].authorId }</a></p>	
</div>


<style>
	.container {
		padding: 0 1.2em;
		justify-content: center;
		text-align: center;
	}

	.viewInfo {
		width: 100%;
		display:  inline-flex;
		justify-content: left;
		align-items: center;
		color: #999;
		font-size: .8em;
		margin: .8em;
	}

	.viewInfo > p {
		margin-left: .5em;
	}


	.wrapper {
		text-align: center;
	}
	.description {
		border-top: 1px solid red;
		margin: .8em;
		padding: .5em;
		font-weight: 300;
	}

	img {
		height: auto;
		max-width: 90%;
		display: inline-block;
		border-radius: 5px;
		margin-bottom: 2em;
	}

	h2 {
		font-size: 1.8em;
		font-weight: 900;
		line-height: 1em;
		text-align: left;
		margin: 0 .5em;
		color: #023047;
	}

	a {
		color: inherit;
	}
</style>