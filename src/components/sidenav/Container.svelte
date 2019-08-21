<script>
	export let appStatus;

	import SidenavHeader from './Header.svelte';
	import Layer from './Layer.svelte';
</script>

<nav class="fixed top-0 left-0 w-64 h-full bg-white shadow-lg">
	<SidenavHeader />
	<Layer {appStatus} />
</nav>