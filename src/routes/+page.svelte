<script lang="ts">
	import profile_image from '$lib/images/profile-image.jpeg';
	import facebook from '$lib/images/facebook.svg';
	import linkedln from '$lib/images/linkedin.svg';
	import instagram from '$lib/images/instagram.svg';
	import github from '$lib/images/github.svg';
	import cv from '$lib/pdf/Babajide_Williams_CV.pdf';
	import Button from './Button.svelte';
	import Modal from './Modal.svelte';
	import ContactForm from './ContactForm.svelte';

	let showModal = false;

	const resume: Record<string, any> = {
		firstname: 'Babajide',
		surname: 'Williams',
		introMessage:
			'I’m a solution-driven software engineer with over 10 years of experience in the IT world, providing a permanent solution to day-to-day challenges that gives the company a competitive edge and producing outstanding results for clients. My experience spans multiple aspects of the design and development process, with a primary focus on creating intuitive, accessible, and user-centered products. I’ve worked closely with designers to translate wireframes and prototypes into interactive, responsive interfaces, ensuring a smooth and engaging user journey across various devices. I concentrate on optimizing user flow and minimizing friction by simplifying navigation, enhancing load times, and ensuring consistent visual and interactive elements',
		email: 'babanila@yahoo.com',
		address: 'Berlin, Germany',
		phoneNumber: '+49 176 301 720 22',
		skype: 'al.babanila',
		facebook: 'https://www.facebook.com/Babanila/',
		github: 'https://github.com/babanila',
		linkedln: 'https://www.linkedin.com/in/babanila/',
		instagram: 'https://www.instagram.com/babanila/',
		thread: 'https://www.threads.net/@babanila',
		education: '',
		f: ''
	};
	const socialConnections = [
		{ name: 'github', icon: github },
		{ name: 'linkedln', icon: linkedln },
		{ name: 'facebook', icon: facebook },
		{ name: 'instagram', icon: instagram }
	];
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Babajide CV" />
</svelte:head>

<section id="home" class="section-part">
	<div class="two-column">
		<div class="column left">
			<slot name="left">
				<div class="column-wrapper">
					<h1><span class="point">I am {resume.firstname} {resume.surname}</span></h1>
					<div class="opacity-box">
						<p>{resume.introMessage}</p>
					</div>

					<div class="my-info">
						<p>
							<span class="span-title">Phone</span>
							<span>{resume.phoneNumber}</span>
						</p>
						<p>
							<span class="span-title">Email</span>
							<span>{resume.email}</span>
						</p>
						<p>
							<span class="span-title">Address</span>
							<span>{resume.address}</span>
						</p>
						<p>
							<span class="span-title">Social</span>
							{#each socialConnections as sc}
								<span class="span-icons">
									<a target="_blank" href={resume[sc.name]} class="icons-wrapper">
										<img src={sc.icon} alt={sc.name} class="icon-svg" />
									</a>
								</span>
							{/each}
						</p>
					</div>

					<div class="about-btns">
						<Button class="primary sm" on:click={() => (showModal = true)}>Contact me</Button>

						<a download="Babajide_Wiliams_CV.pdf" target="_blank" href={cv}>
							<Button class="danger sm" on:click={() => {}}>Download CV</Button>
						</a>
					</div>
				</div>
			</slot>
		</div>
		<div class="column right">
			<slot name="right">
				<div class="column-wrapper">
					<picture>
						<img src={profile_image} alt="profile_image" class="img-responsive" />
					</picture>
				</div>
			</slot>
		</div>
	</div>

	<Modal bind:showModal>
		<ContactForm />
	</Modal>
</section>

<section>
	<div class="corner">
		<a href="https://github.com/Babanila/babajide-williams-website">
			<img src={github} alt="GitHub" />
		</a>
	</div>
</section>

<style>
	.section-part {
		width: 100%;
		display: flex;
		flex: 1;
		border-bottom: 1px solid #e3e3e3;
		margin-top: 80px;
		padding: 32px 0;
	}

	.two-column {
		display: flex;
		flex-wrap: wrap;
	}

	.column-wrapper {
		padding: 10px;
		gap: 16px;
	}

	.left {
		width: auto;
		max-width: 50%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		order: 1;
		font-size: 16px;
		font-family: Roboto, sans-serif;
		animation-name: slideInLeft;
	}

	.opacity-box {
		margin-bottom: 16px;
	}

	.right {
		width: auto;
		max-width: 50%;
		display: flex;
		justify-content: center;
		align-items: center;
		order: 2;
	}

	.img-responsive {
		box-sizing: border-box;
		position: relative;
		min-height: 1px;
		width: 100%;
		float: right;
	}

	.span-title {
		margin-right: 16px;
		text-transform: uppercase;
	}

	.span-icons {
		margin-right: 16px;
	}

	section {
		width: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
		border-bottom: 1px solid #e3e3e3;
	}

	h1 {
		width: 100%;
	}
</style>
