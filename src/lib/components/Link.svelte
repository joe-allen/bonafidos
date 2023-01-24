<script>
	export let href, target, title, className;
</script>
<a on:click|preventDefault class="b-link {className}" href="{href}" target={target ? target : ''}>{title}</a>
<style lang="scss">
	.b-link {
		--background-color: transparent;
		position: relative;
		flex-shrink: 0;
		color: #fff;
		margin-bottom: 0;

		&--nav-item {
			font-weight: 700;
			text-transform: uppercase;
		}

		&::after {
			content: '';
			position: absolute;
			bottom: -1px;
			right: 0;
			transform-origin: right;
			width: 100%;
			height: 1px;
			background: #fff;
			transition: var(--transition) width;
		}

		&::before {
			content: '';
			position: absolute;
			left: 0;
			top: -1px;
			width: 0;
			height: 1px;
			background: #fff;
			transition: var(--transition) width;
		}

		&:focus,
		&:hover {
			--background-color: transparent;
			color: #fff;
			text-decoration: none;
		}

		&:focus::after,
		&:hover::after {
			width: 0;
		}

		&:focus::before,
		&:hover::before {
			width: 100%;
		}
	}

	@media screen and (max-width: map-get($breakpoints, 'lg')) {
		.b-link--nav-item {
			display: none;
		}
	}
</style>