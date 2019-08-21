<script>
	export let appHover, appFocus, modalStatus, lastElement;

	import { get } from 'svelte/store';
	import Element from './Element.svelte';
	import LayerItem from '../sidenav/LayerItem.svelte';
	import DeleteButton from './Delete.svelte';

	let hidden, 
	curFocus,
	curFocusEl,
	isEdit, 
	newElTag,
	newElId, 
	newElClass,
	newElContent;

	modalStatus.subscribe(value => {
		hidden = (value == null);
		isEdit = (value == 'edit');
		curFocusEl = document.getElementsByClassName('builderEl-' + curFocus)[0];

		newElTag = (isEdit ? curFocusEl.tagName.toLowerCase() : 'div');
		newElId = (isEdit ? curFocusEl.id : '');
		newElClass = (isEdit ? curFocusEl.className : '');
		newElContent = (isEdit ? curFocusEl.innerHTML : '');
	});

	appFocus.subscribe(value => {
		curFocus = value;
	});

	function createLayer(el) {
		const newLayer = new LayerItem({
			target: document.getElementById('layerContainer'),
			props: {
				id: el,
				appHover,
				appFocus
			}
		});

		const delBtn = new DeleteButton({
			target: document.getElementById('layerItem-' + el).childNodes[0],
			props: {
				id: el
			}
		});
	}

	function createElement() {
		lastElement.update(n => n + 1);

		const newEl = new Element({
			target: curFocusEl,
			props: {
				builderId: (get(lastElement)),
				tag: newElTag,
				id: newElId,
				classes: ('builderEl-' + get(lastElement) + ' ') + newElClass,
				content: newElContent,
				appHover,
				appFocus			
			}
		});

		newElTag = 'div';
		newElId = '';
		newElClass = '';
		newElContent = '';
		createLayer(get(lastElement));
		handleCancel();
	}

	function mountReplace(Component, options) {
	    const frag = document.createDocumentFragment();
	    const component = new Component({ ...options, target: frag });

	    options.target.parentNode.replaceChild(frag, options.target);

	    return component;
	}

	function updateElement() {	
		const options = {
			target: curFocusEl,
			props: {
				builderId: curFocus,
				tag: newElTag,
				id: newElId,
				classes: ('builderEl-' + curFocus + ' ') + newElClass,
				content: newElContent,
				appHover,
				appFocus			
			}
		}
		mountReplace(Element, options)
		handleCancel();
	}

	function handleSave() {
		if(isEdit) {
			updateElement();
		} else {
			createElement();
		}
	}

	function handleCancel() {
		modalStatus.set(null);
	}
</script>

<style>
	.modal {
		transform: translate(-50%,-50%);
	}

	.overlay {
		background-color: rgba(0,0,0,.5);
	}
</style>

<div class:hidden class="overlay absolute inset-0 w-full h-full"></div>
<div class:hidden class="modal absolute top-1/2 left-1/2 w-128 bg-white rounded shadow-lg">
	<div class="w-full h-16 flex items-center justify-center border-b border-gray-300">
		<h1 class="text-lg font-bold text-gray-700">
			{#if isEdit}
				Edit Layer #{curFocus}
			{:else}
				Create Element on Layer #{curFocus}
			{/if}
		</h1>
	</div>
	<div class="w-full px-4 py-4">
		<div class="flex flex-col justify-center mb-3">
			<label for="newElTag" class="font-bold text-gray-700">Tag</label>
			<input id="newElTag" type="text" class="bg-gray-300 rounded h-10 px-4 mt-2" bind:value={newElTag}/>
		</div>
		<div class="flex flex-col justify-center mb-3">
			<label for="newElId" class="font-bold text-gray-700">Id</label>
			<input id="newElId" type="text" class="bg-gray-300 rounded h-10 px-4 mt-2" bind:value={newElId}/>
		</div>
		<div class="flex flex-col justify-center mb-3">
			<label for="newElClass" class="font-bold text-gray-700">Class</label>
			<input id="newElClass" type="text" class="bg-gray-300 rounded h-10 px-4 mt-2" bind:value={newElClass}/>
		</div>
		<div class="flex flex-col justify-center mb-3">
			<label for="newElContent" class="font-bold text-gray-700">Content</label>
			<textarea id="newElContent" class="bg-gray-300 rounded h-20 py-2 px-4 mt-2 resize-none" bind:value={newElContent}></textarea>			
		</div>
		<button class="w-full h-10 bg-blue-500 font-bold text-white rounded my-1" on:click={handleSave}>
			Save
		</button>
		<button class="w-full h-10 bg-red-500 font-bold text-white rounded my-1" on:click={handleCancel}>
			Cancel
		</button>
	</div>
</div>