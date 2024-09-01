<script>
	import { page } from '$app/stores';
	const items = ['Skills', 'Experience', 'Education', 'Portfolio', 'Contact'];

	let isMenuOpen = false;

	const toggleMenu = () => {
		isMenuOpen = !isMenuOpen;
	};
</script>

<header>
	<div class="logo-name">
		<a href="https://github.com/babanila"> Babajide. </a>
	</div>

	<nav class="desktop-menu">
		<ul>
			<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
				<a href="/">Home</a>
			</li>
			{#each items as item}
				<li aria-current={$page.url.pathname.startsWith('#{item}') ? 'page' : undefined}>
					<a href="#{item}">{item}</a>
				</li>
			{/each}
		</ul>
	</nav>

	<div class="menu-icon" role="button" tabindex="-1" on:keypress={() => {}} on:click={toggleMenu}>
		&#9776;
	</div>

	{#if isMenuOpen}
		<nav class="mobile-menu">
			<ul>
				<li aria-current={$page.url.pathname === '/' ? 'page' : undefined}>
					<a href="/" on:click={toggleMenu}>Home</a>
				</li>
				{#each items as item}
					<li aria-current={$page.url.pathname.startsWith('#{item}') ? 'page' : undefined}>
						<a href="#{item}" on:click={toggleMenu}>{item}</a>
					</li>
				{/each}
			</ul>
		</nav>
	{/if}
</header>

<style>
	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 16px 0;
		border-bottom: 1px solid #e3e3e3;
		background-color: #ffffff;
		color: var(--color-text);
		font-size: 16px;
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		z-index: 5;
	}

	.logo-name {
		width: auto;
		display: flex;
		justify-content: center;
		align-items: center;
		padding-left: 16px;
		font-size: xx-large;
		font-weight: 700;
	}

	.logo-name a {
		color: var(--color-text);
	}

	nav ul {
		list-style-type: none;
		display: flex;
		flex-direction: column;
	}

	nav ul li {
		font-size: 16px;
		cursor: pointer;
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 8px;
		color: var(--color-text);
		font-weight: 700;
		font-size: 12.8px;
		text-transform: uppercase;
		text-decoration: none;
	}

	a:hover {
		color: #3a86ff;
	}

	.menu-icon {
		display: none;
		font-size: 32px;
		cursor: pointer;
		margin-right: 16px;
	}

	.mobile-menu {
		width: 100%;
		display: none;
		flex-direction: column;
		position: absolute;
		top: 60px;
		right: 0;
		background-color: #ffffff;
		border: 1px solid #e3e3e3;
		z-index: 1000;
	}

	.mobile-menu ul {
		list-style-type: none;
		padding: 16px;
	}

	.mobile-menu ul li {
		display: flex;
		justify-content: center;
		align-items: center;
		padding: 16px 0;
		text-align: center;
		font-size: 19.2px;
	}

	@media (max-width: 768px) {
		nav.desktop-menu {
			display: none;
		}

		.menu-icon {
			display: block;
		}

		.mobile-menu {
			display: flex;
		}
	}

	@media (min-width: 769px) {
		.mobile-menu {
			display: none;
		}

		nav ul {
			flex-direction: row;
			padding: 0px;
			margin-right: 16px;
		}

		nav a {
			font-size: 16px;
		}
	}
</style>
