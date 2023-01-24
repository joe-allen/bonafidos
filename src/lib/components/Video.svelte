<script>
	import { onMount } from "svelte";
	import { gsap } from 'gsap';
	import ScrollTrigger from 'gsap/ScrollTrigger';

	const video = 'img/bone-a-fido-flow--short.mp4';
	const img1 = 'img/account.jpg';
	const img2 = 'img/inbox.jpg';

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		const video = document.querySelector('.b-video');
		const videoInner1 = video.querySelector('.b-video__inner:nth-of-type(1)');
		// const videoInner2 = video.querySelector('.b-video__inner:nth-of-type(2)');
		// const videoInner3 = video.querySelector('.b-video__inner:nth-of-type(3)');

		// gsap.set(videoInner2, {opacity: 0, x: 24});
		// gsap.set(videoInner3, {opacity: 0, x: 24});
		const tlVideo = gsap.timeline({
			ease: 'power1.easeOut',
			scrollTrigger: {
				trigger: video,
				start: 'top top',
				pin: true,
				scrub: .2,
				onEnter: () => {
					document.querySelector('.b-svg path').style.fill = '#eeb91b';
				},
				onEnterBack: () => {
					document.querySelector('.b-svg path')?.removeAttribute('style');
				},
			}
		});

		ScrollTrigger.matchMedia({
			"(min-width: 1px)": () => {
				tlVideo.to(videoInner1, {
					opacity: 1
				});
			}
		});

		// ScrollTrigger.matchMedia({
		// 	"(min-width: 1px)": () => {
		// 		tlVideo.to(videoInner1, {
		// 			opacity: 1
		// 		});
		// 	}
		// })

	})
</script>

<section class="b-video">
	<div class="b-video__inner">
		<div class="b-video__video-wrap">
			<video class="b-video__video" playsinline loop autoplay muted src="{video}"></video>
		</div>
	</div>
	<!-- <div class="b-video__inner">
		<div class="b-video__video-wrap">
			<img src="{img1}" width="375" height="812" alt="account screen" class="b-video__video">
		</div>
	</div>
	<div class="b-video__inner">
		<div class="b-video__video-wrap">
			<img src="{img2}" width="375" height="812" alt="inbox screen" class="b-video__video">
		</div>
	</div> -->
</section>

<style lang="scss">
	.b-video {
		position: absolute;
		display: flex;
		justify-content: center;
		align-items: center;
		top: 100vh;
		left: 0;
		height: 100vh;
		width: 100%;
		// pointer-events: none;

		&__title {
			text-align: center;
			max-width: 500px;
			font-weight: 700;
			font-stretch: 80%;
			line-height: 1.2;
			margin: 0 auto;
		}

		&__video-wrap {
			content: '';
			position: absolute;
			top: 57.5%;
			left: 50%;
			transform: translate(-50%, -50%);
			width: clamp(250px, 20vw, 500px);
			box-shadow: 2px 2px 64px rgba(0,0,0,.5);
			aspect-ratio: 266px / 577px;

			&::after {
				content: '';
				position: absolute;
				top: 50%;
				left: 50%;
				transform: translate(-50%, -50%);
				background: var(--primary-hover);
				width: calc(100% + 16px);
				height: calc(100% + 16px);
				border-radius: 32px;
				z-index: -1;
			}
		}

		&__inner {
			transform: translateY(-16px);
			// opacity: 0;
		}

		&__video {
			max-width: 500px;
			object-fit: cover;
			width: 100%;
			aspect-ratio: 266px / 577px;
			border-radius: 24px;

		}

		&__img {
			position: absolute;
			bottom: 0;
			left: 0;
			width: clamp(200px, 22vw, 900px);

			&--right {
				right: 0;
				left: auto;
			}
		}
	}

	@media screen and (max-width: map-get($breakpoints, 'lg')) {
		.b-video {
			&__video-wrap {
				width: clamp(165px, 15vw, 500px);
			}
		}
	}

	@media screen and (max-width: map-get($breakpoints, 'md')) {
		.b-video {
			&__inner {
				transform: translateY(16px);
			}
		}
	}
</style>