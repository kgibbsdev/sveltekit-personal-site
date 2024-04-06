<!-- ImageBox.svelte -->
<script>
	// Import statements
	import { onMount } from 'svelte';
	import Modal from './Modal.svelte';

	// Component definition
	export let imageUrl;
	export let title = 'Runescape';
	let showImage = true;
	let showModal = false; // Initialize showModal as false

	// Function to toggle image visibility
	function toggleImage() {
		showImage = !showImage;
	}

	// Function to open modal
	function openModal() {
		showModal = true; // Set showModal to true when opening modal
	}

	// Run code when component is mounted
	onMount(() => {
		// Preload image for better performance
		const image = new Image();
		image.src = imageUrl;
	});
</script>

<!-- Component markup -->
<div class="image-box" on:mouseenter={toggleImage} on:mouseleave={toggleImage} on:click={openModal}>
	<div class="image-wrapper">
		{#if showImage}
			<img src={imageUrl} alt={title} />
		{/if}
		<div class="color-box" class:show={!showImage}>
			<h2>{title}</h2>
		</div>
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
	<img
		src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExc2FlenBsYjU1MHMwcXY5dzd0dWQ2bjFudW80ZDN6cWJpY2p4ZXo3MiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/26tPo9rksWnfPo4HS/giphy.gif"
	/>
</Modal>

<style>
	/* CSS styles for the component */
	.image-box {
		width: 394px; /* Adjust the width to make it smaller */
		height: 250px; /* Set the height equal to width to make it a square */
		position: relative;
		overflow: hidden;
		cursor: pointer; /* Add cursor pointer to indicate clickability */
	}

	.image-wrapper {
		width: 100%;
		height: 100%;
		position: relative;
	}

	img {
		width: 100%;
		height: 100%;
		display: block;
		object-fit: cover;
	}

	.color-box {
		background-color: lightblue;
		width: 100%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		position: absolute;
		top: 0;
		left: 0;
		opacity: 0;
		transition: opacity 0.3s ease;
	}

	.color-box.show {
		opacity: 1;
	}
</style>
