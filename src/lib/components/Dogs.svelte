<script>
	import Pill from "./Pill.svelte";

	import { onMount } from "svelte";
	import { gsap } from 'gsap';
	import ScrollTrigger from 'gsap/ScrollTrigger';
	import debounce from "just-debounce-it";

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);
		const mobile = window.matchMedia('(max-width: 550px)');
		const dogs = document.querySelectorAll('.b-dogs__img');
		const pills = document.querySelectorAll('.b-dogs__pill-item');

		const tlHero = gsap.timeline({
			ease: 'power1.easeOut',
			scrollTrigger: {
				trigger: dogs[0],
				start: 'bottom top',
				markers: false,
				scrub: 1,
				onEnterBack: () => {
					[...pills].forEach(item => {
						item.classList.remove('b-dogs__pill-item--active')
					})
				}
			}
		});

		ScrollTrigger.matchMedia({
			"(min-width: 1px)": () => {
				tlHero.to(dogs[0], {
					xPercent: 50,
					onComplete: () => {
						if (!mobile.matches) {
							setTimeout(() => {
								pills[0].classList.add('b-dogs__pill-item--active')
							}, 3000);
						}
					}
				}).to(dogs[1], {
					xPercent: -50,
					onComplete: () => {
						if (!mobile.matches) {
							setTimeout(() => {
								pills[1].classList.add('b-dogs__pill-item--active')
							}, 3500);
						}
					}
				}, '-=.25');
			}
		});


		window.addEventListener('scroll', () => {
			const removePills = debounce(() => {
				if (window.scrollY !== 0) {
					return
				}

				// just in case remove pills
				// if at 0 scrollY
				pills[0].classList.remove('b-dogs__pill-item--active')
				pills[1].classList.remove('b-dogs__pill-item--active')

			}, 3000);
			removePills();
		});

	});

	const img = {
		left: 'img/b-mascot__dog--left.png',
		right: 'img/b-mascot__dog--right.png',
	}
</script>

<section class="b-dogs">
	<div class="b-dogs__inner">
		<img class="b-dogs__img b-dogs__img--left" src="{img.left}" alt="dog">
		<img class="b-dogs__img b-dogs__img--right" src="{img.right}" alt="dog">
		<ul class="b-dogs__pill-list">
			<li class="b-dogs__pill-item">
				<Pill title="This looks legit." className="b-pill--accent" />
			</li>
			<li class="b-dogs__pill-item">
				<Pill title="Yeah, I hope my owner signs me up!" className="b-pill--primary-hover" />
			</li>
		</ul>
	</div>
</section>

<style lang="scss">
	.b-dogs {
		position: fixed;
		top: 0;
		left: 0;

		&__pill-list {
			position: relative;
			list-style: none;
			padding-left: 0;
			display: flex;
			align-items: flex-end;
			justify-content: space-around;
			width: 100%;
			height: 100%;
			margin-bottom: 20vw;
			gap: 12px;
			z-index: 111;
		}

		&__pill-item {
			list-style: none;
			opacity: 0;
			transition: opacity .2s ease-out;

			&:first-of-type {
				margin-top: -32px;
			}
		}

		&__inner {
			position: absolute;
			display: flex;
			justify-content: center;
			align-items: center;
			top: 0;
			// left: calc(var(--space-xs) * -1);
			height: 100vh;
			width: 100vw;
			pointer-events: none;
		}

		&__img {
			position: absolute;
			pointer-events: all;
			bottom: 0;
			left: 0;
			width: clamp(165px, 32vw, 1000px);
			transform: translateX(-85%);
			transition: transform 1s ease-out;

			&--right {
				right: 0;
				left: auto;
				transform: translateX(85%);
			}

			&:hover {
				transform: translateX(-75%);
			}
			&--right:hover {
				transform: translateX(75%);
			}
		}
	}

	.b-dogs :global(.b-dogs--fixed) {
		position: fixed;
		bottom: 0;
	}
	.b-dogs :global(.b-dogs__pill-item--active) {
		opacity: 1;
	}

	@media screen and (max-width: map-get($breakpoints, 'sm')) {
		.b-dogs {
			&__pill-item {
				&:first-of-type {
					margin-left: 2rem;
					align-self: flex-start;
				}

				&:last-of-type {
					margin-right: 2rem;
					align-self: flex-end;
				}
			}
			&__pill-list {
				flex-direction: column;
				margin-bottom: 100%;
				gap: 1rem;
				align-items: center;
				justify-content: flex-end;
			}
		}
	}
</style>