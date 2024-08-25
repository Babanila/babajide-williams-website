<script lang="ts">
	let buttonProps = {
		class: [$$restProps.class]
	};
</script>

<button on:click on:mouseover on:mouseenter on:mouseleave on:focus {...buttonProps}>
	<slot />
</button>

<style>
	button {
		color: #ffffff;
		border-radius: 6px;
		border: #ffffff;
		padding: 16px;
		cursor: pointer;
	}

	.primary {
		background-color: #4384cd;
	}
	.primary:hover {
		background-color: #1d3557;
	}

	.secondary {
		background-color: #f1faee;
	}
	.secondary:hover {
		background-color: #95db4b;
	}

	.danger {
		background-color: #e86175;
	}
	.danger:hover {
		background-color: #e61232;
	}

	.sm {
		font-size: 1em;
	}

	.lg {
		font-size: 2em;
	}
</style>
