<script>
	export let className;
	export let title;
</script>
<button on:click class="b-btn {className}">{title}</button>

<style lang="scss">
	.b-btn {
		--border-color: none;
		--box-shadow: none;
		--font-weight: 700;
		--border-radius: 4325345px;
		--spacing: 0;
		position: relative;
		align-self: center;
		text-transform: uppercase;
		z-index: 223 !important;

		&:focus,
		&:hover {
			--border-color: none;
			--box-shadow: none;
			--font-weight: 700;
		}

		// SECONDARY
		&--secondary {
			--background-color: var(--secondary);

			&:focus,
			&:hover {
				--background-color: var(--secondary-hover);
			}
		}

		// ACCENT
		&--accent {
			--background-color: var(--accent);
			color: var(--color-inverse);

			&:focus,
			&:hover {
				--background-color: var(--accent-hover);
			}
		}
	}
</style>