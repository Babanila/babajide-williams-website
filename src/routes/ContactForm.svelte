<script lang="ts">
	import Button from './Button.svelte';

	let status = '';
	export let title: string = '';
	export let description: string = '';
	export let submitWord: string = '';

	const handleSubmit = async (
		/** @type {{ currentTarget: HTMLFormElement | undefined; }} */ data:
			| { currentTarget: HTMLFormElement | undefined }
			| undefined
	) => {
		status = 'Submitting...';
		const formData = new FormData(data?.currentTarget);
		const object = Object.fromEntries(formData);
		const json = JSON.stringify(object);

		const response = await fetch('https://api.web3forms.com/submit', {
			method: 'POST',
			headers: {
				'Content-Type': 'application/json',
				Accept: 'application/json'
			},
			body: json
		});
		const result = await response.json();
		if (result.success) {
			console.log(result);
			status = result.message || 'Success';
		}
	};
</script>

<div>{status}</div>

<section class="contact-form">
	<div class="part-one">
		{#if title}
			<div class="contact-title"><h1>{title}</h1></div>
		{/if}
		{#if description}
			<div class="contact-description">{description}</div>
		{/if}
	</div>

	<div class="part-two">
		<form on:submit|preventDefault={handleSubmit}>
			<input type="hidden" name="access_key" value={import.meta.env.VITE_WEB3FORMS_ACCESS_KEY111} />
			<div class="input-wrapper">
				<div class="input-first">
					<input type="text" name="name" placeholder="Name" required />
					<input type="email" name="email" placeholder="Email" required />
				</div>
				<textarea name="message" placeholder="Message" required rows="3"></textarea>
			</div>
		</form>
		<div class="button-group">
			<Button class="primary sm" on:click={() => handleSubmit}>
				{#if submitWord}
					{submitWord}
				{:else}
					Send Message
				{/if}
			</Button>
		</div>
	</div>
</section>

<style>
	form {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.input-wrapper {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		gap: 32px;
	}

	.input-first {
		display: flex;
		flex-direction: column;
		justify-content: space-between;
		gap: 32px;
	}

	.button-group {
		display: flex;
		justify-content: center;
		margin-top: 16px;
	}

	.contact-title {
		font-size: 24px;
		font-weight: bold;
		margin-bottom: 16px;
	}

	.contact-description {
		font-size: 16px;
		margin-bottom: 32px;
		text-align: center;
	}

	input {
		height: 50px;
		width: 300px;
		border: 1px solid #e3e3e3;
		border-radius: 2px;
		padding: 0 20px;
	}

	textarea {
		height: 100px;
		width: 300px;
		border: 1px solid #e3e3e3;
		padding: 15px 20px;
		resize: none;
		display: block;
		border-radius: 2px;
	}

	@media (min-width: 768px) {
		form {
			display: flex;
			justify-content: center;
			align-items: center;
		}

		.input-wrapper {
			flex-direction: row;
			gap: 32px;
		}

		.input-first {
			gap: 0;
		}

		.button-group {
			justify-content: end;
			margin-top: 16px;
		}
	}
</style>
