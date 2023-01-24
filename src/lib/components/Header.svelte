<script>
	import Logo from "./Logo.svelte";
	import Button from "./Button.svelte";
	import Link from "./Link.svelte";

	function openMenu(e) {

		e.preventDefault();
		const { body } = document;
		const svg = document.querySelector('.b-svg');
		const disclaimer = document.querySelector('.b-disclaimer');

		if (body.classList.contains('b-menu--active')) {

			body.classList.remove('b-menu--active')
			svg?.classList.remove('b-svg--active');
			disclaimer?.classList.remove('b-disclaimer--active');
		} else {
			svg?.classList.add('b-svg--active');
			body?.classList.add('b-menu--active');
			disclaimer?.classList.add('b-disclaimer--active');
		}
	}
</script>

<header>
	<Logo />
	<nav>
		<Link	title="Sign Up" href="#" className="b-link--nav-item" on:click={openMenu}/>
		<Button	className="b-btn--accent" title="Login" on:click={openMenu} />
	</nav>
</header>

<style lang="scss">
	header {
		display: flex;
		align-items: center;
		left: 50%;
		transform: translateX(-50%);
		width: calc(100% - (var(--spacing) * 6));
		position: fixed;
		z-index: 4;
	}

	nav {
		display: flex;
		align-items: center;
		gap: calc(var(--spacing) * 2);
		margin-left: auto;
		flex-shrink: 0;
	}

	@media screen and (max-width: map-get($breakpoints, 'lg')) {
		header {
			display: flex;
		}
	}

	@media screen and (max-width: map-get($breakpoints, 'sm')) {
		header {
			width: calc(100% - (var(--spacing) * 2.5));
		}
	}
</style>