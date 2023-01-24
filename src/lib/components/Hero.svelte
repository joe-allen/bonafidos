<script>
	import { onMount } from "svelte";
	import { gsap } from 'gsap';
	import ScrollTrigger from 'gsap/ScrollTrigger';


	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);
		const hero = document.querySelector('.b-hero');
		const heroInner = document.querySelector('.b-hero__inner');

		const tlHero = gsap.timeline({
			ease: 'power1.easeOut',
			scrollTrigger: {
				trigger: hero,
				start: 'center center',
				pin: true,
				markers: false,
				scrub: 0,
			}
		});

		ScrollTrigger.matchMedia({
			"(min-width: 1px)": () => {
				tlHero.to(heroInner, {
					opacity: 0,
				});
			}
		});

	})
</script>

<section class="b-hero">
	<div class="b-hero__inner">
		<h2 class="b-hero__title">Find Caretakers You Can Trust.</h2>
		<span class="b-hero__arrow"></span>
	</div>
</section>

<style lang="scss">
	.b-hero {
		position: absolute;
		display: flex;
		justify-content: center;
		align-items: center;
		top: 0;
		left: 0;
		height: 100vh;
		width: 100%;
		pointer-events: none;

		&__title {
			text-align: center;
			max-width: 550px;
			font-weight: 700;
			font-stretch: 80%;
			line-height: 1.2;
			margin: 0 auto;
		}

		&__arrow {
			position: absolute;
			top: calc(100% - 48px);
			left: 50%;
			transform: translate(-50%, -50%) rotate(135deg);
			width: 24px;
			height: 24px;
			border-right: 2px solid #fff;
			border-top: 2px solid #fff;
			animation-name: float;
			animation-duration: 3s;
			animation-iteration-count: infinite;
		}

		@keyframes float {
			0% {
				transform: translate(-50%, calc(-50% - 16px)) rotate(135deg);
			}
			50% {
				transform: translate(-50%, -50%) rotate(135deg);
			}
			100% {
				transform: translate(-50%, calc(-50% - 16px)) rotate(135deg);

			}
		}
	}

	@media screen and (max-width: map-get($breakpoints, 'md')) {
		.b-hero {
			&__title {
				padding-inline: var(--space-l);
			}
		}
	}
</style>