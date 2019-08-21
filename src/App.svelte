<script>
	import { writable } from 'svelte/store';
	import Sidenav from './components/sidenav/Container.svelte';
	import Builder from './components/builder/Bootstrapper.svelte';

	const appStatus = {
		appHover: writable(null),
		appFocus: writable(null)
	}

	const lastElement = writable(0);

	const modalStatus = writable(null);
</script>

<Sidenav {appStatus} />
<Builder {appStatus} {modalStatus} {lastElement} />
