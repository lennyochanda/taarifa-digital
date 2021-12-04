<script>
	export let post
	import View16 from 'carbon-icons-svelte/lib/View16'
	import { Tag } from 'carbon-components-svelte'

	const generateColor = () => {
		const colors = [
			"red",
			"magenta",
			"purple",
			"blue",
			"cyan",
			"teal",
			"green",
			"gray",
			"cool-gray",
			"warm-gray",
			"high-contrast"
		]

		return colors[Math.floor(Math.random() * colors.length)]
	}
</script>

<div class="post">
	<Tag type={ generateColor() }>tag</Tag>
	<Tag type={ generateColor() }>tag</Tag>
	<Tag type={ generateColor() }>tag</Tag>


	<h2>{post.title.substring(0, 30)}</h2>
	<p>{post.body.substring(0, 150)}</p>
	<div class="cardFooter">
		<div class="viewInfo">
			<View16 />
			<p>2000</p>
		</div>
		<p class="link">
			<a sveltekit:prefetch href={`/posts/${post.id}`}>Read More</a>
		</p>
	</div>
</div>

<style>
	.post {
		border-radius: 8px;
		padding: 1em;
		box-shadow: 0 4px 10px #bbb;
		background: #fff;
	}

	.viewInfo {
		display:  inline-flex;
		align-items: center;
	}

	.cardFooter {
		display: flex;
		justify-content: space-between;
		margin: 0;
		padding: .5em;
	}

	h2 {
		margin: 0;
		padding: .2em;
		font-size: 1.4em;
		font-weight: 600;
		color: #023047;
	}

	.link {
		text-align: right;
	}

	p {
		padding-left: 5px;
		color: #343a40;
		line-height: 130%;
	}
</style>