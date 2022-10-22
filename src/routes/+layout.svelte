<script>
	import '../app.scss';
	import '../styles/global.scss';
	import { page } from '$app/stores';

	let menuOpen = false;

	const links = [
		{
			name: 'Home',
			href: '/'
		},
		{
			name: 'T-Shirt Printing',
			href: '/shirts'
		},
		{
			name: 'Attendance',
			href: 'https://cap.ridgecompsci.club'
		},
		{
			name: 'RidgeHacks',
			href: 'https://ridgehacks.us'
		}
	];

	let viewing;
	$: viewing = links.find((link) => link.href === $page.url.pathname);
</script>

<main class:menuOpen>
	<button class="material-icons menuButton" on:click={(_) => (menuOpen = !menuOpen)}
		>{menuOpen ? 'close' : 'menu'}</button
	>
	<div class="mobileHeader">
		<span class="mobileName">
			RCSC<br />
			<span style="font-weight: 200; text-transform: none;">
				<span style="font-weight: 500;">#</span>
				{viewing.name}
			</span>
		</span>
	</div>
	<div class="menu">
		<h1>Ridge <br /> Computer <br /> Science <br /> Club</h1>
		{#each links as link}
			<a
				href={link.href}
				class:active={$page.url.pathname === link.href}
				on:click={(_) => (menuOpen = false)}>{link.name}</a
			>
		{/each}
	</div>
	<div class="content">
		<slot />
	</div>
</main>

<style lang="scss">
	main {
		display: flex;
		width: 100%;
		max-width: 1300px;
		// gap: min(4vw, 64px);
		gap: 24px;
		padding: 24px;
		margin-block: 32px;
		--menu-transition: 350ms cubic-bezier(0.39, -0.01, 0.05, 1.03);
	}
	.menu {
		position: sticky;
		top: 24px;
		align-self: flex-start;
		text-align: right;
		max-width: 250px;
		transition: var(--menu-transition);
		* {
			margin: 0;
		}
		h1 {
			font-size: 2rem;
			margin-bottom: 16px;
			line-height: 0.9em;
			font-weight: 900;
			text-transform: uppercase;
			color: var(--accent);
		}
		display: flex;
		flex-direction: column;
		gap: 8px;
		a {
			text-decoration: none;
			padding: 8px;
			border-radius: 12px;
			color: var(--text-muted);
			transition: var(--hover-transition);
			&:hover {
				background-color: var(--fg);
				color: var(--text);
			}
			&.active {
				background-color: var(--accent-fg);
				color: var(--accent);
			}
		}
	}
	.content {
		display: flex;
		flex: 1;
		flex-direction: column;
		// margin-top: 32px;
		gap: 16px;
		transition: var(--menu-transition);
		> :global(*) {
			margin: 0;
		}
	}
	.mobileHeader {
		display: none;
		transition: var(--menu-transition);
	}
	.menuButton {
		display: none;
		transition: var(--menu-transition);
	}
	@media (max-width: $mobile-threshold) {
		main {
			gap: 0;
			flex-direction: column;
			margin-top: 0;
		}
		.mobileHeader {
			display: flex;
			justify-content: space-between;
			align-items: center;
			margin-bottom: 16px;
			height: 48px;
			.mobileName {
				font-size: 1em;
				font-weight: 900;
				text-transform: uppercase;
				max-width: 200px;
				color: var(--accent);
			}
		}
		.menuButton {
			display: block;
			height: 48px;
			aspect-ratio: 1;
			border: none;
			background: var(--accent);
			color: var(--accent-text);
			border-radius: 8px;
			position: fixed;
			top: 24px;
			right: 24px;
			box-shadow: 0 0 12px -2px var(--bg);
			z-index: 20;
		}
		.content {
			width: 100%;
			flex: 0;
		}
		.menu {
			position: fixed;
			z-index: 10;
			top: 0;
			left: 0;
			width: 100vw;
			max-width: 100vw;
			height: 100vh;
			// background-color: var(--bg);
			padding: 24px;
			padding-top: calc(24px * 2 + 48px);
			transform: translateX(100%);
		}
		.menuOpen {
			.menu {
				transform: translateX(0);
			}
			.content,
			.mobileHeader {
				filter: blur(26px) grayscale(1);
				opacity: 0.1;
			}
		}
	}
</style>
