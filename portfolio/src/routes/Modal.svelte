<!-- Modal.svelte -->
<script>
	export let showModal; // boolean

	let dialog; // HTMLDialogElement

	$: if (dialog && showModal) dialog.showModal();
</script>

<dialog
	bind:this={dialog}
	on:close={() => (showModal = false)}
	on:click|self={() => dialog.close()}
>
	<div on:click|stopPropagation>
		<!-- Modal header -->
		<div class="modal-header">
			<slot name="header" />
		</div>
		<hr />

		<!-- Modal body -->
		<div class="modal-body">
			<slot />
			<img src="path_to_your_gif.gif" alt="GIF" style="max-width: 100%; height: auto;" />
		</div>
		<hr />

		<!-- Modal footer -->
		<div class="modal-footer">
			<button autofocus on:click={() => dialog.close()}>Close modal</button>
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
		animation: zoom-out 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
	}

	dialog::backdrop {
		background: rgba(0, 0, 0, 0.3);
	}

	dialog[open] {
		animation: zoom-in 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
	}

	@keyframes zoom-in {
		from {
			transform: scale(0.95);
		}
		to {
			transform: scale(1);
		}
	}

	dialog[open]::backdrop {
		animation: fade 0.2s ease-out;
	}

	@keyframes fade {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}

	button {
		display: block;
	}
</style>
