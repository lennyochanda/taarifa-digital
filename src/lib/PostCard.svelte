<script>
	export let post
	import Time16 from 'carbon-icons-svelte/lib/Time16'

	import { Tag } from 'carbon-components-svelte'
</script>

<div class="post">
	{#each post.tags as tag}
		<Tag type="cool-gray">{tag}</Tag>
	{/each}


	<h2>{post.title}</h2>
	<div class="cardFooter">
		<div class="viewInfo">
			<Time16 />
			<p>{post.readTime} min read</p>
		</div>
		<p>
			<a sveltekit:prefetch href={`/posts/${post.id}`}>Read More</a>
		</p>
	</div>
</div>

<style>
	.post {
		border-radius: .7rem;
		padding: .5em;
		box-shadow: 5px 5px 8px #bbb;
		background-color: #eee;
		transition: transform 500ms ease;
	}

	.post:hover,
	.post:focus,
	.post:focus-within {
		transform: scale(1.02);
	}

	.viewInfo {
		display:  inline-flex;
		align-items: center;
		color: #ff0000;
	}

	.cardFooter {
		display: flex;
		justify-content: space-between;
		margin: 0;
		padding: .5em;
	}

	.viewInfo > p {
		color: #023047;
	}

	h2 {
		margin: .4em 0;
		padding: .2em;
		font-size: 1.3em;
		font-weight: 500;
		color: #023047;
		border-top: 1px dotted #ddd;
	}

	p {
		padding: 0 5px;
		color: #343a40;
		font-size: .9em;
	}

	a {
		text-align: right;
		color: #ff0000;
		font-size: 1em;
	}
</style>