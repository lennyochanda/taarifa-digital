<script>
  import '../app.css'

  import Navbar from '$lib/Navbar.svelte'
  import Sidebar from '$lib/Sidebar.svelte'
  import Footer from '$lib/Footer.svelte'

	let open = false
</script>

<Sidebar bind:open />
<Navbar bind:sidebar={open}/>

<div class="container">
	<slot></slot>
</div>

<Footer />

<style>
	.container {
		max-width: 800px;
		margin: .5em auto;
	}
</style>