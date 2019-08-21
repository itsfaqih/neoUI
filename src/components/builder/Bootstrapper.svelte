<script>
	export let appStatus, modalStatus, lastElement;

	import Container from './Container.svelte';
	import AddButton from './Add.svelte';
	import EditButton from './Edit.svelte';
	import Modal from './Modal.svelte';
</script>

<Container {...appStatus} />
<EditButton {...appStatus} {modalStatus} />
<AddButton {...appStatus} {modalStatus} />
<Modal {...appStatus} {modalStatus} {lastElement}/>