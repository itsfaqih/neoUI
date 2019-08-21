<script>
	export let appHover, appFocus;

	import Element from './Element.svelte';

	let curHover, curFocus;

	appHover.subscribe(value => {
		curHover = value;
	})

	appFocus.subscribe(value => {
		curFocus = value;
	})
</script>

<main class="flex-1 h-screen ml-64 p-1 bg-white">
	<div class:active={curHover == 0 || curFocus == 0} class="builderEl-0 w-full h-full">
	</div>
</main>