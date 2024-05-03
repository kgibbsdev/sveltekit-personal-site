<!-- Modal.svelte -->
<script>
	export let showModal; // boolean

	let dialog; // HTMLDialogElement

	$: if (dialog && showModal) dialog.showModal();
</script>

<dialog bind:this={dialog} on:close={() => (showModal = false)} class="text-center">
	<div>
		<!-- Modal header -->
		<div class="modal-header text-left px-1">
			<slot name="header" />
		</div>
		<hr />

		<!-- Modal body -->
		<div class="modal-body">
			<slot />
		</div>
		<hr />

		<!-- Modal footer -->
		<div class="modal-footer">
			<button
				class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-lg shadow-md
        "
				autofocus
				on:click={() => dialog.close()}>Close modal</button
			>
		</div>
	</div>
</dialog>

<style>
	/* Styles for the modal */
	/* Add your styles here */

	dialog {
		max-width: 32em;
		border-radius: 0.2em;
		border: none;
		padding: 0;
	}

	dialog::backdrop {
		background: rgba(0, 0, 0, 0.3);
	}

	dialog[open] {
		animation: zoom-in 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
	}
</style>
