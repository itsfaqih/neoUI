<script>
	export let appHover, appFocus, modalStatus;

	let curFocus;

	appFocus.subscribe(value => {
		curFocus = value;
	});

	function handleClick() {
		curFocus != null && modalStatus.set('edit');
	}
</script>

<div class="fixed bottom-8 right-32">
	<button id="builderEdit" class:active={curFocus != null} class="w-10 h-10 flex items-center justify-center rounded-full focus:outline-none" on:click={handleClick}>
		<i class="material-icons text-base text-white">
			edit
		</i>
	</button>
</div>