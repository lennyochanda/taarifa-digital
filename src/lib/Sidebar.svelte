<script>
	export let open = false
	import Breakpoint from 'carbon-components-svelte/src/Breakpoint/Breakpoint.svelte'
	import { page } from '$app/stores'
	let size
	let events = []
</script>

<Breakpoint bind:size on:match={e => (events = [...events, e.detail])} />

{#if size === "sm" || size === "md"}
	<aside class="absolute w-full h-full border-r-2 shadow-lg" class:open>
		<nav class="p-14 text-xl">
			<a class="block" on:click={() => open = !open} class:active={$page.path === "/" || $page.path === "/posts/*"} sveltekit:prefetch href="/">
				Featured
			</a>
			<a class="block" on:click={() => open = !open} class:active={$page.path === "/entertainment"} sveltekit:prefetch href="entertainment">
				Entertainment
			</a>
			<a class="block" on:click={() => open = !open} class:active={$page.path === "/sports"} sveltekit:prefetch href="sports">
				Sports
			</a>
			<a class="block" on:click={() => open = !open} class:active={$page.path === "/business"} sveltekit:prefetch href="business">
				Business
			</a>
			<a class="block" on:click={() => open = !open} class:active={$page.path === "/lifestyle"} sveltekit:prefetch href="lifestyle">
				Lifestyle
			</a>
			<a class="block" on:click={() => open = !open} class:active={$page.path === "/technology"} sveltekit:prefetch href="technology">
				Technology
			</a>
			<a class="block" on:click={() => open = !open} class:active={$page.path === "/about"} sveltekit:prefetch href="about">
				About
			</a>
		</nav>
	</aside>
{/if}

<style>
	aside {
		left: -100%;
		transition: left 0.3s ease-in-out;
		background-color: #fff;
		z-index: 21;
	}
	
	.open {
		left: 0
	}

	a {
		padding-bottom: .2em;
		margin-bottom: .2em;
		font-weight: 500;
		color: #023047;
	}

	.active {
		border-bottom: .8px solid red;
	}
</style>