<script>
	import { page } from '$app/stores';
</script>

<header>
	<div class="logo-name">
		<a href="https://github.com/babanila"> Babajide. </a>
	</div>

	<nav>
		<ul>
			<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
				<a href="/">Home</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('#skills') ? 'page' : undefined}>
				<a href="#skills">Skills</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('#experience') ? 'page' : undefined}>
				<a href="#experience">Experience</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('#education') ? 'page' : undefined}>
				<a href="#education">Education</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('#portfolio') ? 'page' : undefined}>
				<a href="#portfolio">Portfolio</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('#portfolio') ? 'page' : undefined}>
				<a href="#portfolio">Feedback</a>
			</li>
			<li aria-current={$page.url.pathname.startsWith('#contact') ? 'page' : undefined}>
				<a href="#contact-me">Contact Me</a>
			</li>
		</ul>
	</nav>
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		padding: 16px 0;
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		z-index: 5;
		border-bottom: 1px solid #e3e3e3;
		background: #f1faee;
		font-size: 16px;
	}

	.logo-name {
		width: auto;
		display: flex;
		justify-content: center;
		align-items: center;
		padding-left: 1em;
		font-size: xx-large;
		font-weight: 700;
	}

	.logo-name a {
		color: var(--color-text);
	}

	nav {
		display: flex;
		justify-content: center;
		padding-right: 1em;
	}

	ul {
		position: relative;
		margin: 0;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.5rem;
		color: var(--color-text);
		font-weight: 700;
		font-size: 0.8rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--color-theme-1);
	}
</style>
