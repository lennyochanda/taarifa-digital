<script context="module">
	import { GraphQLClient, gql, request } from 'graphql-request';
	import { variables } from '$lib/variables'

	export async function load({ page }) {
		const id = `${page.params.id}`
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
	  const { post } = await graphcms.request(QUERY)
	  console.log(post)
		return {
			props: {
				post
			}
		}
	}
</script>

<script>
	export let post
	export let user	
</script>

<h2>me</h2>
<p>me</p>

<p>Written by <a sveltekit:prefetch href={`/authors/`}>me</a></p>