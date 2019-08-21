<script>
	export let id, appHover, appFocus;

	import { get } from 'svelte/store';

	function handleOver() {
		appHover.set(id);
	}

	function handleLeave() {
		appHover.set(null);
	}

	function handleClick() {
		if(get(appFocus) != id) {
			appFocus.set(id);
		} else {
			appFocus.set(null);
		}
	}

	let curHover, curFocus;

	appHover.subscribe(value => {
		curHover = value;
	})

	appFocus.subscribe(value => {
		curFocus = value;
	})
</script>

<li id={"layerItem-" + id} class:active={curHover == id || curFocus == id} class="my-1" on:mouseover={handleOver} on:mouseleave={handleLeave} on:click={handleClick} >
	<div class="w-full h-12 px-4 flex flex-row items-center cursor-pointer">
		<span class="text-gray-600">
			Element #{id}
		</span>
	</div>
</li>