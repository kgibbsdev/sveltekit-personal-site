<script>
	// Import statements
	import { onMount } from 'svelte';
	import Modal from './Modal.svelte';
	// Props
	export let imageUrl;
	export let title = 'NO TITLE';
	export let rounded = false;
	export let imgWidth = 400;
	// Reactive variable for overlay visibility
	let showOverlay = false;

	// Modal visibility
	let showModal = false;

	// Function to open modal
	function openModal() {
		showModal = true;
	}

	// Preload image for better performance
	onMount(() => {
		const image = new Image();
		image.src = imageUrl;
	});
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div
	class="relative overflow-hidden cursor-pointer"
	on:mouseenter={() => (showOverlay = true)}
	on:mouseleave={() => (showOverlay = false)}
	on:click={openModal}
>
	<!-- Note how the image tag needs width set as an attribute -->
	<img class="h-auto" src={imageUrl} alt={title} width={imgWidth} class:rounded-full={rounded} />
	<!-- Compared to the div which needs it added in the style attribute -->
	<div
		class="absolute inset-0 flex justify-center items-center bg-blue-500 text-white"
		style="display: {showOverlay ? 'flex' : 'none'}; width: {`${imgWidth}px`};"
		class:rounded-full={rounded}
	>
		<h2>{title}</h2>
	</div>
</div>

<Modal bind:showModal>
	<h2 slot="header">modal</h2>

	<ol class="definition-list">
		<li>of or relating to modality in logic</li>
		<li>
			containing provisions as to the mode of procedure or the manner of taking effect —used of a
			contract or legacy
		</li>
		<li>of or relating to a musical mode</li>
		<li>of or relating to structure as opposed to substance</li>
		<li>
			of, relating to, or constituting a grammatical form or category characteristically indicating
			predication
		</li>
		<li>of or relating to a statistical mode</li>
	</ol>
</Modal>
