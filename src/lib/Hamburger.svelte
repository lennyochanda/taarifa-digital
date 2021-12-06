<script>
	export let open = false
	import Breakpoint from 'carbon-components-svelte/src/Breakpoint/Breakpoint.svelte'
	let size
	let events = []
</script>

<Breakpoint bind:size on:match={e => (events = [...events, e.detail])} />

{#if size === "sm" || size === "md"}
	<button class="cursor-pointer mr-4 border-none focus:outline-none" class:open on:click={() => open = !open}>
		<svg width=28 height=28>
			<line id="top" x1=0 y1=4  x2=32 y2=4/>
			<line id="middle" x1=0 y1=12 x2=20 y2=12/>
			<line id="bottom" x1=0 y1=20 x2=32 y2=20/>
		</svg>
	</button>
{/if}

<style>
	svg {
		min-height: 24px;
		transition: transform 0.3s ease-in-out;
	}
	
	svg line {
		stroke: currentColor;
		stroke-width: 2.5;
		transition: transform 0.3s ease-in-out;
		border-radius: 8px;
	}
	
	button {
		color: #ff0000;
		z-index: 2;
	}

	button:hover {
		color: #ff0000;
	}
	
	.open svg {
		transform: scale(0.7);
	}
	
	.open #top {
		transform: translate(6px, 0px) rotate(45deg);
	}
	
	.open #middle {
		opacity: 0;
	}
	
  .open #bottom {
		transform: translate(-12px, 11px) rotate(-45deg);
	}
</style>