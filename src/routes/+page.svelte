<script lang="ts">
	import cv from '$lib/pdf/Babajide_Williams_CV.pdf';
	import chat from '$lib/images/chat.svg';
	import facebook from '$lib/images/facebook.svg';
	import github from '$lib/images/github.svg';
	import instagram from '$lib/images/instagram.svg';
	import linkedln from '$lib/images/linkedin.svg';
	import note from '$lib/images/note.svg';
	import recipe from '$lib/images/recipe.svg';
	import schedule from '$lib/images/schedule.svg';
	import search from '$lib/images/search_icon.svg';
	import video from '$lib/images/video.svg';
	import vote from '$lib/images/voting-box.png';
	import weather from '$lib/images/weather.svg';
	import profile_image from '$lib/images/profile-image.jpeg';
	import Button from './Button.svelte';
	import ContactForm from './ContactForm.svelte';
	import Modal from './Modal.svelte';

	type SocialConnectionType = {
		name: string;
		icon: string;
	};

	type SkillType = {
		title: string;
		description: string;
		types: {
			name: string;
			details: string;
		}[];
	};

	type ExperienceType = {
		title: string;
		company: string;
		date: string;
		description: string;
	};

	type EducationType = {
		title: string;
		institution: string;
		date: string;
		description: string;
	};

	type PortfolioItem = {
		title: string;
		serviceType: string;
		date: string;
		imageUrl: string;
		gitUrl: string;
	};

	type ContactType = {
		title: string;
		description: string;
	};

	let showModal = false;

	const home: Record<string, string> = {
		firstname: 'Babajide',
		surname: 'Williams',
		introMessage:
			'I’m a solution-driven software engineer with over 10 years of experience in the IT world, providing a permanent solution to day-to-day challenges that gives the company a competitive edge and producing outstanding results for clients. My experience spans multiple aspects of the design and development process, with a primary focus on creating intuitive, accessible, and user-centered products. I’ve worked closely with designers to translate wireframes and prototypes into interactive, responsive interfaces, ensuring a smooth and engaging user journey across various devices. I concentrate on optimizing user flow and minimizing friction by simplifying navigation, enhancing load times, and ensuring consistent visual and interactive elements',
		email: 'babanila@yahoo.com',
		address: 'Berlin, Germany',
		phone: '+49 176 301 720 22',
		skype: 'al.babanila',
		facebook: 'https://www.facebook.com/Babanila/',
		github: 'https://github.com/babanila',
		linkedln: 'https://www.linkedin.com/in/babanila/',
		instagram: 'https://www.instagram.com/babanila/',
		thread: 'https://www.threads.net/@babanila'
	};

	const infos: string[] = ['phone', 'email', 'address'];

	const socialConnections: SocialConnectionType[] = [
		{ name: 'github', icon: github },
		{ name: 'linkedln', icon: linkedln },
		{ name: 'facebook', icon: facebook },
		{ name: 'instagram', icon: instagram }
	];

	const skills: SkillType = {
		title: 'Skills',
		description:
			'I’m driven by the thrill of collaborating with passionate individuals to bring extraordinary software to life. Creating something exceptional together fuels my creativity and pushes the boundaries of what’s possible.',
		types: [
			{
				name: 'Web Development',
				details:
					'Javascript, Coffeescript, Python, Node.js, Nest.js, SQL, MongoDB, PostgreSQL, WebStorm.'
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

	const experienceDetails: ExperienceType[] = [
		{
			title: 'Senior Frontend Developer',
			company: 'HealthHero GmbH',
			date: 'Sept, 2021 — Present',
			description:
				'Creating advanced software solutions and web applications using React, TypeScript, JavaScript, Node.js, HTML, CSS3, Cypress, Jest, and Storybook, including developing a UI components library. By enhancing user accessibility on websites, I significantly improved the user experience. My optimization efforts resulted in a 200% increase in website speed, a 10% reduction in bundle size, and a reduction in hacker attacks from 2.0% to 0.02%. Additionally, I developed the Long-Covid-App and the Questionnaire Rule Engine tool.'
		},
		{
			title: 'Frontend Developer',
			company: 'EGEOS GmbH (North.io GmbH)',
			date: 'Oct, 2020 — Sept, 2021',
			description:
				'Created software solutions and different web applications for clients using frameworks and technologies like React, Gatsby, Hugo, JavaScript, Nodejs, HTML and CSS3. The optimization of websites resulted in a 300% increase in speed.'
		},
		{
			title: 'Software Engineer',
			company: 'Daizu GmbH',
			date: 'June, 2019 — June, 2020',
			description:
				'Developed questionnaire app, e-commerce, CRM and blog-post website using using technologies such as React, Gatsby, GraphQL, CMS(Sanity), JavaScript,HTML, style-components and pure CSS. Refactored codebase to achieve a 30% reduction in bundle size.'
		},
		{
			title: 'Software Engineer',
			company: 'Commercetools GmbH',
			date: 'June, 2018 — June, 2019',
			description:
				'Developed innovative API solutions using Node.js, CoffeeScript, REST, and GraphQL to create various modules that support modern microservice-based architecture for clients, such as Category Export and Resource Deleter. Additionally, I built full websites and individual web pages for various clients and wrote unit, integration and end-to-end tests for APIs to ensure functionality and reliability.'
		},
		{
			title: 'Software Developer',
			company: 'Bliss Energy Nig. Ltd.',
			date: 'May, 2015 — May, 2018',
			description:
				"I developed innovative software solutions using pure JavaScript, HTML, and CSS, and created various websites utilizing vanilla JavaScript, jQuery, React, HTML, and CSS. I played a key role in setting up the network that enhanced the company's development and growth. Additionally, I initiated market research studies to identify demand for the company's products or services and captured business development opportunities to capitalize on them."
		},
		{
			title: 'System Administrator',
			company: 'Emirates Flight Catering',
			date: 'May, 2012 — May, 2015',
			description:
				'I was responsible for setting up and maintaining Windows Server 2012, managing and configuring routers and switches during network setup, and overseeing user account management. Additionally, I handled the installation, updating, and maintenance of software on office equipment, including computer systems, routers, and switches.'
		},
		{
			title: 'Network Administrator',
			company: 'Yemshba Telephone Network',
			date: 'March, 2010 — Sept, 2012',
			description:
				'I was responsible for setting up and maintaining Windows Server 2008, managing user accounts, and overseeing the installation, updating, and maintenance of software on company systems. Additionally, I handled the installation and upkeep of office equipment, including computer systems, routers, and switches.'
		}
	];

	const educationDetails: EducationType[] = [
		{
			title: 'Master',
			institution: 'University of Applied Science Kiel',
			date: 'Oct, 2016 — Nov, 2020',
			description: 'MSc (Hons) in Information Engineering.'
		},
		{
			title: 'Bachelor',
			institution: 'Federal University of Technology Akure',
			date: 'Oct, 2005 — Nov, 2010',
			description: 'BTech (Hons) in Computer Science.'
		}
	];

	const contactDetails: ContactType = {
		title: 'Contact',
		description:
			'Are you in need of a frontend development expert or working on something exciting? I’d love to help bring it to life! Feel free to drop me a message.'
	};

	const portfolioItems: PortfolioItem[] = [
		{
			title: 'Recipe',
			serviceType: 'backend',
			date: 'Aug 21, 2024',
			imageUrl: recipe,
			gitUrl: 'https://github.com/Babanila/recipe'
		},
		{
			title: 'Video App',
			serviceType: 'full',
			date: 'Jun 3, 2024',
			imageUrl: video,
			gitUrl: 'https://github.com/Babanila/vonage-video-app'
		},
		{
			title: 'Note App',
			serviceType: 'full',
			date: 'Oct 4, 2023',
			imageUrl: note,
			gitUrl: 'https://github.com/Babanila/note-app'
		},
		{
			title: 'Scheduling App',
			serviceType: 'full',
			date: 'Feb 16, 2023',
			imageUrl: schedule,
			gitUrl: 'https://github.com/Babanila/scheduling-app'
		},
		{
			title: 'Search Service',
			serviceType: 'backend',
			date: 'Jun 16, 2020',
			imageUrl: search,
			gitUrl: 'https://github.com/Babanila/search-service'
		},
		{
			title: 'Chat App',
			serviceType: 'frontend',
			date: 'Sep 22, 2019',
			imageUrl: chat,
			gitUrl: 'https://github.com/Babanila/chat-app'
		},
		{
			title: 'Voting App',
			serviceType: 'frontend',
			date: 'Oct 21, 2019',
			imageUrl: vote,
			gitUrl: 'https://github.com/Babanila/voting-app'
		},
		{
			title: 'Weather App',
			serviceType: 'frontend',
			date: 'Nov 15, 2019',
			imageUrl: weather,
			gitUrl: 'https://github.com/Babanila/fut-weather-app'
		}
	];
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Babajide CV" />
</svelte:head>

<section id="Home" class="home-section">
	<div class="two-column">
		<div class="column left">
			<slot name="left">
				<div class="column-wrapper">
					<h1><span class="point">I am {home.firstname} {home.surname}</span></h1>
					<div class="opacity-box">
						<p>{home.introMessage}</p>
					</div>

					<div class="my-info">
						{#each infos as info}
							<p>
								<span class="span-title">{info}</span>
								<span>{home[`${info}`]}</span>
							</p>
						{/each}
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
		<ContactForm
			title="Contact Form"
			description="Are you in need of a frontend development expert or working on something exciting? I’d love
				to help bring it to life! Feel free to drop me a message."
			submitWord="Submit"
		/>
	</Modal>
</section>

<section id="Skills" class="skills-section">
	<h2 class="section-title">{skills.title}</h2>
	<p class="skills-description">{skills.description}</p>

	<div class="skills-grid">
		{#each skills.types as { name, details }}
			<div class="skill-section">
				<h3>{name}</h3>
				<p>{details}</p>
			</div>
		{/each}
	</div>
</section>

<section id="Experience" class="experience-section">
	<div class="content-wrapper">
		<div class="left-column">
			<h2 class="section-title">Experience</h2>
			<p>
				I collaborate with startups, established organizations, and companies across the health,
				e-commerce, retail, and SaaS sectors to develop digital solutions that empower clients to
				tackle challenges and foster meaningful connections with millions of users daily.
			</p>
		</div>
		<div class="right-column">
			{#each experienceDetails as experience}
				<div class="experience-item">
					<h2 class="section-inner-title">
						{experience.title} <span class="company">{experience.company}</span>
					</h2>
					<p class="date">{experience.date}</p>
					<p class="description">{experience.description}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<section id="Education" class="education-section">
	<div class="content-wrapper">
		<div class="left-column">
			<h2 class="section-title">Education</h2>
			<p>
				All my life I have been driven by my strong belief that education is important. I try to
				learn something new every single day.
			</p>
		</div>
		<div class="right-column">
			{#each educationDetails as edu (edu.title)}
				<div class="experience-item">
					<h2 class="section-inner-title">{edu.title}</h2>
					<p class="education-institution">{edu.institution}</p>
					<p class="description">{edu.description}</p>
					<p class="date">{edu.date}</p>
				</div>
			{/each}
		</div>
	</div>
</section>

<section id="Portfolio" class="portfolio-section">
	<h2 class="section-title">Portfolio</h2>
	<div class="filter-menu">
		<a href="#">All Project</a>
		<a href="#">Frontend</a>
		<a href="#">Backend</a>
		<a href="#">Full Websites</a>
	</div>
	<div class="portfolio-grid">
		{#each portfolioItems as item}
			<a target="_blank" href={item.gitUrl} class="portfolio-anchor">
				<div class="portfolio-item">
					<img src={item.imageUrl} alt={item.title} />
					<h3>{item.title}</h3>
					<p>{item.date}</p>
				</div>
			</a>
		{/each}
	</div>
</section>

<section id="Contact" class="contact-section">
	<div class="content-wrapper">
		<div class="left-column">
			<h2 class="section-title">{contactDetails.title}</h2>
			<p>
				{contactDetails.description}
			</p>
		</div>
		<div class="right-column">
			<ContactForm />
		</div>
	</div>
</section>

<style>
	.home-section {
		padding: 20px;
		max-width: 1200px;
		margin: 0 auto;
		margin-top: 60px;
		/* border-bottom: 1px solid #e3e3e3; */
	}

	.two-column {
		display: flex;
		flex-direction: column-reverse;
		gap: 20px;
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
		font-size: 40px;
		margin-bottom: 16px;
	}

	.opacity-box {
		margin-bottom: 32px;
		opacity: 0.9;
	}

	.my-info p {
		margin: 8px 0;
		display: flex;
		align-items: center;
		gap: 32px;
	}

	.span-title {
		font-weight: bold;
		text-transform: capitalize;
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
		margin-top: 40px;
	}

	.img-responsive {
		max-width: 100%;
		height: auto;
		border-radius: 50%;
		border: 2px solid #ddd;
	}

	.section-title {
		font-size: 32px;
		font-weight: bold;
		margin-bottom: 8px;
	}

	.skills-section {
		display: flex;
		flex-direction: column;
		align-items: center;
		padding: 40px 20px;
		text-align: center;
	}

	.skills-description {
		font-size: 20px;
		margin-bottom: 32px;
		max-width: 600px;
	}

	.skills-grid {
		display: grid;
		grid-template-columns: 1fr;
		gap: 24px;
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
		font-size: 20px;
		margin-bottom: 12px;
	}

	.skill-section p {
		font-size: 16px;
		line-height: 1.5;
	}

	.contact-section,
	.education-section,
	.experience-section {
		padding: 40px 20px;
		max-width: 1200px;
		margin: 0 auto;
	}

	.section-inner-title {
		font-weight: bold;
	}

	.content-wrapper {
		display: flex;
		flex-direction: column;
		gap: 20px;
	}

	.left-column {
		flex: 1;
	}

	.right-column {
		flex: 2;
	}

	.experience-item {
		margin-bottom: 20px;
		border-bottom: 1px solid #e3e3e3;
	}

	.company {
		color: #666666;
		font-weight: normal;
		font-style: italic;
	}

	.date {
		color: #666666;
		font-size: 16px;
	}

	.description {
		margin-top: 5px;
	}

	h1 {
		font-size: 32px;
		margin-bottom: 16px;
	}

	.filter-menu {
		display: flex;
		flex-direction: column;
		align-items: flex-start;
		gap: 8px;
		margin-bottom: 32px;
	}

	.filter-menu a {
		text-decoration: none;
		color: #000;
		font-weight: bold;
	}

	.filter-menu a:hover {
		color: #3a86ff;
	}

	.portfolio-section {
		padding: 40px 120px;
		display: flex;
		flex-direction: column;
		margin: 0 auto;
	}

	.portfolio-grid {
		max-width: 400px;
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
		gap: 32px;
	}

	.portfolio-anchor {
		text-decoration: none;
		color: #1d3557;
	}
	.portfolio-anchor:hover {
		color: #3a86ff;
	}

	.portfolio-item {
		box-shadow: 0px 4px 12px rgba(0, 0, 0, 0.1);
		border-radius: 8px;
		overflow: hidden;
		background: #fff;
		transition: transform 0.2s;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		padding: 16px 0;

	}

	.portfolio-item img {
		width: 100px;
		height: 100px;
		/* height: auto; */
		/* display: block; */
	}

	.portfolio-item:hover {
		transform: translateY(-5px);
	}

	.portfolio-item h3 {
		margin: 16px;
		font-size: 20px;
	}

	.portfolio-item p {
		margin: 0 16px 16px;
		color: #666;
	}

	/* Medium screens (tablets) */
	@media (min-width: 768px) {
		.two-column {
			flex-direction: row;
			gap: 40px;
		}

		h1 {
			font-size: 48px;
		}

		.column.right {
			justify-content: flex-end;
		}
		.skills-grid {
			grid-template-columns: 1fr 1fr;
		}

		.content-wrapper {
			flex-direction: row;
			gap: 40px;
		}

		.filter-menu {
			flex-direction: row;
			gap: 16px;
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

		.content-wrapper {
			gap: 60px;
		}

		.portfolio-grid {
			max-width: 1200px;
			display: grid;
			grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
			gap: 32px;
		}
	}
</style>
