<script>
	export let title;
	export let className;
</script>

<div class="b-pill {className}">
	<div class="b-pill__inner">
		<div class="b-pill__title">
			{title}
		</div>
	</div>
</div>

<style lang="scss">
	.b-pill {
		position: relative;
		padding: .25rem var(--space-2xs);
		display: inline-flex;
		background: var(--primary);
		color: #fff;
		font-size: 16px;
		line-height: 1;
		border-radius: 48px;

		&--primary-hover {
			color: var(--color);
			background: var(--primary-hover);
		}

		&--secondary {
			color: var(--color-inverse);
			background: var(--secondary);
		}

		&--accent {
			color: var(--color-inverse);
			background: var(--accent);
		}
	}
</style>