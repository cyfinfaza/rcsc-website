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
			name: 'RidgeHacks',
			href: '/ridgehacks'
		}
		// {
		// 	name: 'Registration Form',
		// 	href: 'https://tally.so/r/3xX1qk'
		// },
		// {
		// 	name: 'Attendance',
		// 	href: 'https://cap.ridgecompsci.club'
		// }
		// {
		// 	name: 'RidgeHacks',
		// 	href: 'https://ridgehacks.us'
		// }
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
				{viewing?.name ?? ''}
			</span>
		</span>
	</div>
	<div class="menu" style="animation-delay: 50ms;">
		<h1>Ridge <br /> Computer <br /> Science <br /> Club</h1>
		{#each links as link}
			<a
				href={link.href}
				class:active={$page.url.pathname === link.href}
				on:click={(_) => (menuOpen = false)}>{link.name}</a
			>
		{/each}
		<div class="socials">
			<a href="mailto:ridgecompsci@ridgehacks.us"
				><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 40 40" class="svelte-pyh3eb"
					><path
						d="M6.542 34.583Q4.708 34.583 3.417 33.25Q2.125 31.917 2.125 30.167V9.833Q2.125 8.042 3.417 6.708Q4.708 5.375 6.542 5.375H33.458Q35.292 5.375 36.604 6.708Q37.917 8.042 37.917 9.833V30.167Q37.917 31.917 36.604 33.25Q35.292 34.583 33.458 34.583ZM20 22.125Q20.292 22.125 20.562 22.042Q20.833 21.958 21.208 21.75L32.792 14.083Q33.042 13.917 33.25 13.583Q33.458 13.25 33.458 12.75Q33.458 11.958 32.667 11.417Q31.875 10.875 31.083 11.458L20 18.708L8.958 11.458Q8.167 10.958 7.354 11.396Q6.542 11.833 6.542 12.75Q6.542 13.208 6.75 13.542Q6.958 13.875 7.25 14.083L18.792 21.75Q19.167 21.958 19.438 22.042Q19.708 22.125 20 22.125Z"
					/></svg
				></a
			>
			<a href="https://classroom.google.com/u/0/c/NzcyNzgzNjkzNDNa?cjc=lu7yltb"
				><svg
					xmlns="http://www.w3.org/2000/svg"
					x="0px"
					y="0px"
					viewBox="0 0 32 32"
					style=" fill:#FFFFFF;"
					><path
						d="M 7 5 C 5.355469 5 4 6.355469 4 8 L 4 24 C 4 25.644531 5.355469 27 7 27 L 25 27 C 26.644531 27 28 25.644531 28 24 L 28 8 C 28 6.355469 26.644531 5 25 5 Z M 7 7 L 25 7 C 25.566406 7 26 7.433594 26 8 L 26 24 C 26 24.566406 25.566406 25 25 25 L 23 25 L 23 23 L 18 23 L 18 25 L 7 25 C 6.433594 25 6 24.566406 6 24 L 6 8 C 6 7.433594 6.433594 7 7 7 Z M 16 11 C 14.894531 11 14 11.894531 14 13 C 14 14.105469 14.894531 15 16 15 C 17.105469 15 18 14.105469 18 13 C 18 11.894531 17.105469 11 16 11 Z M 11.5 13 C 10.671875 13 10 13.671875 10 14.5 C 10 15.328125 10.671875 16 11.5 16 C 12.328125 16 13 15.328125 13 14.5 C 13 13.671875 12.328125 13 11.5 13 Z M 20.5 13 C 19.671875 13 19 13.671875 19 14.5 C 19 15.328125 19.671875 16 20.5 16 C 21.328125 16 22 15.328125 22 14.5 C 22 13.671875 21.328125 13 20.5 13 Z M 16 16 C 14.453125 16 13.394531 16.660156 12.75 17.21875 C 12.414063 17.09375 12.039063 17 11.59375 17 C 9.902344 17 9 18 9 18 L 9 20 L 23 20 L 23 18 C 23 18 22.082031 17 20.59375 17 C 20.082031 17 19.644531 17.089844 19.28125 17.21875 C 18.636719 16.65625 17.558594 16 16 16 Z"
					/></svg
				></a
			>
			<a href="https://discord.com/invite/57bQ9X5"
				><svg
					xmlns="http://www.w3.org/2000/svg"
					x="0px"
					y="0px"
					viewBox="0 0 72 72"
					style=" fill:#000000;"
					><path
						d="M54.657,19.077c0,0,8.343,9.663,8.343,27.069v3.65c0,0-10.536,6.866-13.747,6.866l-3.115-4.529	c1.936-0.867,4.577-2.372,4.577-2.372l-0.965-0.747c0,0-6.173,2.86-13.749,2.86s-13.749-2.86-13.749-2.86l-0.965,0.747	c0,0,2.641,1.505,4.577,2.372l-3.115,4.529C19.536,56.662,9,49.796,9,49.796v-3.65c0-17.406,8.343-27.069,8.343-27.069	s5.707-2.762,10.977-3.489l1.635,3.1c0,0,2.599-0.602,6.045-0.602s6.045,0.602,6.045,0.602l1.635-3.1	C48.95,16.315,54.657,19.077,54.657,19.077z M27.01,43.603c2.656,0,4.808-2.418,4.808-5.401c0-2.983-2.153-5.401-4.808-5.401	s-4.808,2.418-4.808,5.401C22.202,41.185,24.354,43.603,27.01,43.603z M44.99,43.603c2.656,0,4.808-2.418,4.808-5.401	c0-2.983-2.153-5.401-4.808-5.401c-2.656,0-4.808,2.418-4.808,5.401C40.182,41.185,42.334,43.603,44.99,43.603z"
					/></svg
				></a
			>
			<a href="https://www.instagram.com/ridgecompsciclub/"
				><svg
					xmlns="http://www.w3.org/2000/svg"
					x="0px"
					y="0px"
					viewBox="0 0 24 24"
					style=" fill:#000000;"
				>
					<path
						d="M 8 3 C 5.243 3 3 5.243 3 8 L 3 16 C 3 18.757 5.243 21 8 21 L 16 21 C 18.757 21 21 18.757 21 16 L 21 8 C 21 5.243 18.757 3 16 3 L 8 3 z M 8 5 L 16 5 C 17.654 5 19 6.346 19 8 L 19 16 C 19 17.654 17.654 19 16 19 L 8 19 C 6.346 19 5 17.654 5 16 L 5 8 C 5 6.346 6.346 5 8 5 z M 17 6 A 1 1 0 0 0 16 7 A 1 1 0 0 0 17 8 A 1 1 0 0 0 18 7 A 1 1 0 0 0 17 6 z M 12 7 C 9.243 7 7 9.243 7 12 C 7 14.757 9.243 17 12 17 C 14.757 17 17 14.757 17 12 C 17 9.243 14.757 7 12 7 z M 12 9 C 13.654 9 15 10.346 15 12 C 15 13.654 13.654 15 12 15 C 10.346 15 9 13.654 9 12 C 9 10.346 10.346 9 12 9 z"
					/></svg
				></a
			>
		</div>
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
		gap: var(--padding-1);
		padding: var(--padding-1);
		margin-block: 32px;
		--menu-transition: 350ms cubic-bezier(0.39, -0.01, 0.05, 1.03);
	}
	.menu {
		position: sticky;
		top: calc(var(--padding-1) + 32px);
		align-self: flex-start;
		text-align: right;
		max-width: 250px;
		transition: var(--menu-transition);
		max-height: calc(100vh - var(--padding-1));
		overflow: auto;
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
		.socials {
			display: flex;
			flex-wrap: wrap;
			gap: 8px;
			justify-content: flex-end;
			margin-top: 8px;
			a {
				width: 54px;
				aspect-ratio: 1;
				display: flex;
				align-items: center;
				justify-content: center;
				border-radius: 50%;
				background-color: var(--fg);
				svg {
					width: 32px;
					height: 32px;
					&,
					* {
						fill: var(--text);
					}
				}
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
	.menu,
	.content {
		animation: slideIn 0.5s cubic-bezier(0, 0.61, 0.25, 1) backwards;
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
			top: var(--padding-1);
			right: var(--padding-1);
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
			padding: var(--padding-1);
			padding-top: calc(var(--padding-1) * 2 + 48px);
			transform: translateX(100%);
			animation: none;
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
	@keyframes slideIn {
		0% {
			transform: translateY(200px);
			opacity: 0;
		}
	}
</style>
