<script>
	export let appStatus;

	import LayerItem from './LayerItem.svelte';	
</script>

<div class="w-full px-4 mt-4">
	<h1 class="font-semibold text-gray-600 mb-2">
		Layer
	</h1>
	<ul id="layerContainer" class="w-full">
		<LayerItem id={0} {...appStatus} />
	</ul>
</div>