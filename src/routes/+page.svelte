<script>
	import Hero from "$lib/components/Hero.svelte";
	import Video from "$lib/components/Video.svelte";
	import Dogs from "$lib/components/Dogs.svelte";

	export let data;
</script>

<Hero />
<Video />
<Dogs />
<svg class="b-svg" id="visual" viewBox="0 0 900 600" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><g transform="translate(465.31371558678825 274.02444821390264)"><path d="M164.8 -157.9C196.6 -132.9 193.8 -66.5 180.1 -13.7C166.5 39.1 141.9 78.3 110.1 122.9C78.3 167.6 39.1 217.8 -10.6 228.4C-60.3 239 -120.7 210 -159 165.3C-197.3 120.7 -213.7 60.3 -218.9 -5.2C-224 -70.7 -218.1 -141.4 -179.8 -166.4C-141.4 -191.4 -70.7 -170.7 -2.1 -168.6C66.5 -166.5 132.9 -182.9 164.8 -157.9" fill="#082d9b"></path></g></svg>
<div class="b-disclaimer"><p>Demo purposes only.<br>View the <a class="b-disclaimer__link" href="https://dribbble.com/shots/20446911-BONE-A-FIDOS" target="_blank">casestudy</a>.</p></div>

<!--
<h1>{data.post.title}!</h1>
<img src={data.post.avatar} alt=""> -->

<style lang="scss">
	.b-svg {
		position: fixed;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		width: 100vw;
		z-index: -1;
		transition: transform .7s ease-out;
		pointer-events: none;

		path {
			transition: fill 2s ease-out;
		}
	}

	.b-disclaimer {
		position: fixed;
		left: 50%;
		transform: translate(-50%, 8px);
		opacity: 0;
		pointer-events: none;
		display: flex;
		text-align: center;
		width: 100%;
		justify-content: center;
		align-items: center;
		height: 75vh;
		transition: transform 1s .1s ease-out, opacity .4s ease-out;
		z-index: 3 !important;
		font-weight: 900 !important;

		&__link {
			color: var(--accent) !important;
			transition: color .2s ease-out;
		}

		&__link:hover {
			color: var(--accent-hover) !important;
		}
	}

@media screen and (max-width: 768px) {
	.b-svg {
		width: 175vw;
		top: 60%;
	}

	:global(.b-disclaimer--active) {
		height: 85vh !important;
	}
}
</style>