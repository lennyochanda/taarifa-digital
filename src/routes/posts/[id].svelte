<script context="module">
	import { GraphQLClient, gql, request } from 'graphql-request';
	import { variables } from '$lib/variables'
	import { page } from '$app/stores'

	export async function load({ page }) {
	  const graphcms = new GraphQLClient(variables.baseUrl,
	  {
	  	headers: {}
	  });

		const QUERY = gql`
	    {
	      posts(where: {id: "${page.params.id}"}) {
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
	  console.log(QUERY)
	  const post = await graphcms.request(QUERY)
	  console.log(post)
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

	const title = post.posts[0].title
	const src = post.posts[0].image[0].url
	const desc = post.posts[0].description[0]
	const readTime = post.posts[0].readTime
	const author = post.posts[0].authorId
	const publishDate = post.posts[0].published.slice(0, 10)
	const publishTime = post.posts[0].published.slice(11, 16)
	const content = post.posts[0].content[0].html
	console.log(content)
</script>

<div class="container">
	<h2>{title}</h2>
	<div class="viewInfo">
		<p>Written by <a href="/authors">{author}</a> on {publishDate} at {publishTime}</p>
	</div>

	<p class="description">
		{desc}
	</p>

	<div class="wrapper">
		<img {src} alt="About this post">
	</div>
	<p>{@html content}</p>

	<h2>About {author}</h2>

	<p>by <a sveltekit:prefetch href={`/authors/`}>me</a></p>	
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
		color: #ff0000;
		font-size: .8em;
		margin: .8em;
		margin-top: 2.5em;
	}

	.viewInfo > p {
		color: #023047;
		font-style: italic;
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
		max-width: 80%;
		display: inline-block;
		border-radius: 5px;
		margin-bottom: 2em;
	}

	h2 {
		font-size: 2em;
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