<script lang="ts">
	import Button from './Button.svelte';

	let status = '';
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

<section class="contact-body">
	<div class="contact-title">
		<h1><span class="point">Contact Form</span></h1>
	</div>
	<div class="contact-description">
		<p>
			Are you in need of a frontend development expert or working on something exciting? I’d love to
			help bring it to life! Feel free to drop me a message.
		</p>

		<form on:submit|preventDefault={handleSubmit}>
			<input type="hidden" name="access_key" value={import.meta.env.VITE_WEB3FORMS_ACCESS_KEY} />
			<div class="input-wrapper">
				<input type="text" name="name" placeholder="Name" required />
				<input type="email" name="email" placeholder="Email" required />
				<textarea name="message" placeholder="Message" required rows="3"></textarea>
				<div class="button-group">
					<Button class="primary sm" on:click={() => handleSubmit}>Submit</Button>
				</div>
				<div class="info-group">
					<div>{status}</div>
				</div>
			</div>
		</form>
	</div>
</section>

<style>
	.contact-body {
		width: auto;
		min-width: 400px;
		padding: 20px;
	}

	.input-wrapper {
		display: flex;
		flex-direction: column;
		gap: 32px;
	}

	input {
		height: 50px;
		border: 1px solid #e3e3e3;
		border-radius: 2px;
		padding: 0 20px;
	}

	textarea {
		height: 130px;
		border: 1px solid #e3e3e3;
		padding: 15px 20px;
		resize: none;
		display: block;
		border-radius: 2px;
	}

	.info-group,
	.button-group {
		display: flex;
		justify-content: center;
		gap: 16px;
	}
</style>
