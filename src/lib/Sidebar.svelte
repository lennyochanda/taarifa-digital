<script>
	export let open = false
	import Breakpoint from 'carbon-components-svelte/src/Breakpoint/Breakpoint.svelte'
	let size
	let events = []
</script>

<Breakpoint bind:size on:match={e => (events = [...events, e.detail])} />

{#if size === "sm" || size === "md"}
	<aside class="absolute w-full h-full border-r-2 shadow-lg" class:open>
		<nav class="p-12 text-xl">
			<a class="block" sveltekit:prefetch href="/">Featured</a>
			<a class="block" sveltekit:prefetch href="#entertainment">Entertainment</a>
			<a class="block" sveltekit:prefetch href="#sports">Sports</a>
			<a class="block" sveltekit:prefetch href="#business">Business</a>
			<a class="block" sveltekit:prefetch href="#lifestyle">Lifestyle</a>
			<a class="block" sveltekit:prefetch href="#technology">Technology</a>
			<a class="block" sveltekit:prefetch href="#contact">Contact</a>
		</nav>
	</aside>
{/if}

<style>
	aside {
		left: -100%;
		transition: left 0.3s ease-in-out;
		z-index: 19;
		background-color: #fff;
	}
	
	.open {
		left: 0
	}

	a {
		padding-bottom: .5em;
		font-weight: 500;
		color: #023047;
	}
</style>