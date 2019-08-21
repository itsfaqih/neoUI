<script>
	export let id;

	function handleClick() {
		const layerContainer = document.getElementById('layerContainer');
		const elementContainer = document.getElementsByClassName('builderEl-' + 0)[0];
		const layerItem = document.getElementById('layerItem-' + id);
		const element = document.getElementsByClassName('builderEl-' + id)[0];

		layerContainer.removeChild(layerItem);
		elementContainer.removeChild(element);
	}
</script>

<button class="ml-auto w-8 h-8 flex items-center justify-center bg-red-500 rounded-full focus:outline-none" on:click={handleClick}>
	<i class="material-icons text-base text-white">
		delete
	</i>
</button>