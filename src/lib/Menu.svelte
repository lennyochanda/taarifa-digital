<script>
	import Breakpoint from 'carbon-components-svelte/src/Breakpoint/Breakpoint.svelte'
	let size
	let events = []
</script>

<Breakpoint bind:size on:match={e => (events = [...events, e.detail])} />

{#if size === "lg"}
	<nav class="hidden flex text-gray-500 uppercase text-bold sm:block">
	  <a href="/" class="hover:text-gray-700 hover:no-underline">
	  	Featured
	  </a>

		<a href="/entertainment" class="hover:text-gray-700 hover:no-underline">
			Entertainment
		</a>

		<a href="/sports" class="hover:text-gray-700 hover:no-underline">
			Sports
		</a>

		<a href="/business" class="hover:text-gray-700 hover:no-underline">
			Business
		</a>

		<a href="/lifestyle" class="hover:text-gray-700 hover:no-underline">
			Lifestyle
		</a>

		<a href="/technology" class="hover:text-gray-700 hover:no-underline">
			Technology
		</a>

		<a href="/contact" class="hover:text-gray-700 hover:no-underline">
			Contact
		</a>
	</nav>
{/if}