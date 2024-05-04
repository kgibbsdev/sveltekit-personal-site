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
		<div class="">
			<slot />
		</div>
		<hr />

		<!-- Modal footer -->
		<div class="">
			<a href="#_" class="relative inline-block text-lg group">
				<span
					class="relative z-10 block px-5 py-3 overflow-hidden font-medium leading-tight text-gray-800 transition-colors duration-300 ease-out border-2 border-gray-900 rounded-lg group-hover:text-white"
				>
					<span class="absolute inset-0 w-full h-full px-5 py-3 rounded-lg bg-gray-50"></span>
					<span
						class="absolute left-0 w-48 h-48 -ml-2 transition-all duration-300 origin-top-right -rotate-90 -translate-x-full translate-y-12 bg-gray-900 group-hover:-rotate-180 ease"
					></span>
					<span class="relative" on:click={() => dialog.close()}>Button Text</span>
				</span>
				<span
					class="absolute bottom-0 right-0 w-full h-12 -mb-1 -mr-1 transition-all duration-200 ease-linear bg-gray-900 rounded-lg group-hover:mb-0 group-hover:mr-0"
					data-rounded="rounded-lg"
				></span>
			</a>
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
