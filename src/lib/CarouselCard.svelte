<script>
	export let post
	let src = post.image[0].url
</script>

<div class="card" style="background-image: url({src});">
	<div class="card-content">
		<h4 class="card-title">
			{post.title}
		</h4>
		<p class="card-body">
			{post.description}
		</p>
		<a sveltekit:prefetch href={`/posts/${post.id}`} class="button">Read more</a>
	</div>
</div>

<style>
	.card {
		color: #eee;
		background-color: gray;
		background-size: cover;
		padding: 6rem 0 0;
		margin: .5em;
		max-width: 35ch;
		border-radius: .7rem;
		overflow: hidden;
		transition: transform 500ms ease;
	}

	.card:hover,
	.card:focus,
	.card:focus-within {
		transform: scale(1.02);
	}

	.card-content {
		padding: 1.5em;
		background: linear-gradient(
			hsla(0, 0%, 0%, 0),
			hsla(0, 0%, 0%, 0.4) 25%,
			hsla(0, 0%, 0%, 1)
		);
	}

	.card-title {
		font-size: 1.2em;
		font-weight: 900;
	}

	.card-body {
		color: rgb(255, 255, 255 / 0.85);
		font-size: 1em;
		font-weight: 300;
		margin: .5em 0;
		line-height: 1em;
	}

	.button {
		cursor: pointer;
		display: inline-block;
		text-decoration: none;
		color: #eee;
		background-color: #ff0000;
		padding: .7em 1em;
		margin: .4em 0;
		border-radius: .25em;
		font-size: .9em;
	}

	.button:hover,
	.button:focus {
		background-color: #ff7700;
		transform: scale(1.02);
	}
</style>