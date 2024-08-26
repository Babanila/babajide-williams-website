<script lang="ts">
	import closeIcon from '$lib/images/x-mark-circle-lined.svg';

	export let showModal: boolean;
	let dialog: HTMLDialogElement;
	$: if (dialog && showModal) dialog.showModal();
</script>

<!-- svelte-ignore a11y-click-events-have-key-events a11y-no-noninteractive-element-interactions -->
<dialog
	bind:this={dialog}
	on:close={() => (showModal = false)}
	on:click|self={() => dialog.close()}
>
	<!-- svelte-ignore a11y-no-static-element-interactions -->
	<div on:click|stopPropagation>
		<slot name="header" />
		<slot />
		<div class="button-wrapper">
			<img
				src={closeIcon}
				alt="modal-close icon"
				class="close-icon-svg"
				on:click={() => dialog.close()}
			/>
		</div>
	</div>
</dialog>

<style>
	dialog {
		width: auto;
		max-width: 800px;
		border-radius: 3.2px;
		border: none;
		padding: 0;
	}

	dialog::backdrop {
		background: rgba(0, 0, 0, 0.3);
	}

	dialog > div {
		padding: 1em;
	}

	dialog[open] {
		animation: zoom 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
	}

	@keyframes zoom {
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

	.button-wrapper {
		display: flex;
		align-items: center;
		justify-content: center;
		width: 30px;
		height: 30px;
		cursor: pointer;
		position: absolute;
		top: 5px;
		right: 5px;
	}

	.close-icon-svg:hover {
		width: 30px;
		height: 30px;
	}

	.close-icon-svg:hover,
	.button-wrapper:hover {
		display: block;
	}
</style>
