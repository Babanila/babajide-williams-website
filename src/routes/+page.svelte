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

	const home: Record<string, any> = {
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

	const skills = {
		title: 'Skills',
		intro:
			'I’m driven by the thrill of collaborating with passionate individuals to bring extraordinary software to life. Creating something exceptional together fuels my creativity and pushes the boundaries of what’s possible.',
		types: [
			{
				name: 'Web Development',
				details: 'Javascript, Coffeescript, Python, Node.js, Nest.js MongoDB, PostgreSQL, WebStorm.'
			},
			{
				name: 'Frontend Development',
				details:
					'HTML, CSS, LESS, SASS, SCSS, Tailwind, Bootstrap, React, Next.js, Gatsby, Hugo.js, Foundation, Angular.js.'
			},
			{
				name: 'UI/UX Design',
				details:
					'Figma, Photoshop, Sketch, Prototyping, Wireframing, User Research, Usability Testing.'
			},
			{
				name: 'Testing & CI/CD',
				details: 'Storybook, Cypress, Jest, Docker, GitHub-Actions, CircleCI, Jenkins.'
			}
		]
	};
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Babajide CV" />
</svelte:head>

<section id="Home" class="section-part">
	<div class="two-column">
		<div class="column left">
			<slot name="left">
				<div class="column-wrapper">
					<h1><span class="point">I am {home.firstname} {home.surname}</span></h1>
					<div class="opacity-box">
						<p>{home.introMessage}</p>
					</div>

					<div class="my-info">
						<p>
							<span class="span-title">Phone</span>
							<span>{home.phoneNumber}</span>
						</p>
						<p>
							<span class="span-title">Email</span>
							<span>{home.email}</span>
						</p>
						<p>
							<span class="span-title">Address</span>
							<span>{home.address}</span>
						</p>
						<p>
							<span class="span-title">Social</span>
							{#each socialConnections as sc}
								<span class="span-icons">
									<a target="_blank" href={home[sc.name]} class="icons-wrapper">
										<img src={sc.icon} alt={sc.name} class="icon-svg" />
									</a>
								</span>
							{/each}
						</p>
					</div>

					<div class="home-btns">
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

<section id="Skills" class="skills-container">
	<h2 class="skills-title">{skills.title}<span>.</span></h2>
	<p class="skills-description">{skills.intro}</p>

	<div class="skills-grid">
		{#each skills.types as { name, details }}
			<div class="skill-section">
				<h3>{name}</h3>
				<p>{details}</p>
			</div>
		{/each}
	</div>
</section>

<style>
	.section-part {
		padding: 20px;
		max-width: 1200px;
		margin: 0 auto;
		margin-top: 30px;
		/* border-bottom: 1px solid #e3e3e3; */
	}

	.two-column {
		display: flex;
		flex-direction: column;
		gap: 20px;
		color: #666666;
	}

	.column {
		flex: 1;
		padding: 10px;
	}

	.column.left {
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	.column.right {
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.column-wrapper {
		width: 100%;
	}

	h1 {
		font-size: 2.5rem;
		margin-bottom: 1rem;
	}

	.point {
		color: #333333;
	}

	.opacity-box {
		margin-bottom: 2rem;
		opacity: 0.9;
	}

	.my-info p {
		margin: 0.5rem 0;
		display: flex;
		align-items: center;
		gap: 32px;
	}

	.span-title {
		font-weight: bold;
		margin-right: 10px;
	}

	.span-icons {
		margin-top: 10px;
	}

	.icon-svg {
		width: 24px;
		height: 24px;
	}

	.home-btns {
		display: flex;
		gap: 10px;
		margin-top: 20px;
	}

	.img-responsive {
		max-width: 100%;
		height: auto;
		border-radius: 50%;
		border: 2px solid #ddd;
	}

	.skills-container {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 20px;
		text-align: center;
		background-color: azure;
	}

	.skills-title {
		font-size: 2rem;
		font-weight: bold;
		margin-bottom: 0.5rem;
		color: #333;
	}

	.skills-title span {
		color: #1d3557;
	}

	.skills-description {
		font-size: 1.25rem;
		margin-bottom: 2rem;
		color: #666;
		max-width: 600px;
	}

	.skills-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 1.5rem;
		width: 100%;
		max-width: 1200px;
	}

	.skill-section {
		padding: 15px;
		border: 1px solid #ddd;
		border-radius: 8px;
		background-color: #f9f9f9;
	}

	.skill-section h3 {
		font-size: 1.25rem;
		margin-bottom: 0.75rem;
		color: #333;
	}

	.skill-section p {
		font-size: 1rem;
		color: #666;
		line-height: 1.5;
	}

	/* Medium screens (tablets) */
	@media (min-width: 768px) {
		.two-column {
			flex-direction: row;
			gap: 40px;
		}

		h1 {
			font-size: 3rem;
		}

		.column.right {
			justify-content: flex-end;
		}
		.skills-grid {
			grid-template-columns: 1fr 1fr;
		}
	}

	/* Large screens (desktops) */
	@media (min-width: 1024px) {
		.two-column {
			gap: 60px;
		}

		.img-responsive {
			width: 300px;
			height: 300px;
		}
		.skills-grid {
			grid-template-columns: 1fr 1fr 1fr 1fr;
		}
	}

	h1 {
		width: 100%;
	}
</style>
