<script context="module">
	export async function load({ page, fetch }) {
		const id = page.params.authorId

		const [resUser, resPosts] = await Promise.all([
			fetch(`https://jsonplaceholder.typicode.com/users/${id}`),
			fetch("https://jsonplaceholder.typicode.com/posts")
		])
		const user = await resUser.json()
		const allPosts = await resPosts.json()
		const posts = allPosts.filter(post => post.userId === user.id)

		return {
			props: {
				user,
				posts
			}
		}
	}
</script>

<script>
	export let user
	export let posts
</script>

<h2>{user.name}</h2>
<p>{user.email}</p>

<h3>Posts by {user.name}</h3>

<ul>
	{#each posts as post}
		<li>
			<a href={`/posts/${post.id}`}>{post.title}</a>
		</li>
	{/each}
</ul>