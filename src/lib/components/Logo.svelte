<script>
	let logo = 'img/logo.svg';

	const closeMenu = () => {
		const { body } = document;

		if (body.classList.contains('b-menu--active')) {
			const svg = document.querySelector('.b-svg');

			body.classList.remove('b-menu--active')
			svg?.classList.remove('b-svg--active');
		}
	}
</script>
<a href="/" class="b-logo" on:click={closeMenu}>
	<div class="b-logo__wrap">
		<img class="b-logo__logo" src="{logo}" alt="Bone-A-Fidos">
	</div>
	<h1 class="b-logo__title">Bone-A-Fidos</h1>
</a>
<style lang="scss">
	.b-logo {
		display: flex;
		align-items: center;
		gap: var(--spacing);

		&:focus,
		&:hover {
			--background-color: transparent;
			color: #fff;
			text-decoration: none;
		}

		&__wrap {
			position: relative;
			background: var(--primary-hover);
			width: clamp(75px, 2vw, 100px);
			height: clamp(75px, 2vw, 100px);
			border-radius: 50%;
		}

		&__logo {
			width: 100%;
			height: 100%;
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(calc(-50% + 2px), calc(-50% + 9px)) scale(1.5);
			transition: transform var(--transition);
		}

		&:hover &__logo {
			transform: translate(calc(-50% - 2px), calc(-50% + 11px)) scale(2.75) rotate(25deg);
		}

		&__title {
			margin-bottom: 0;
			text-transform: uppercase;
			font-weight: 700;
			// font-variation-settings: "slnt" 12;
			font-size: var(--step--1);
		}
	}
</style>