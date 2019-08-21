<script>
	export let appHover, appFocus, modalStatus;

	let curFocus;

	appFocus.subscribe(value => {
		curFocus = value;
	});

	function handleClick() {
		curFocus != null && modalStatus.set('create');
	}
</script>

<div class="fixed bottom-8 right-16">
	<button id="builderAdd" class:active={curFocus != null} class="w-10 h-10 flex items-center justify-center rounded-full focus:outline-none" on:click={handleClick}>
		<i class="material-icons text-white">
			add
		</i>
	</button>
</div>