<script>
	import ParallaxCard3D from '$lib/cards/ParallaxCard3D.svelte';
</script>

<main>
	<ParallaxCard3D />
</main>

<style>
	main {
		width: 100vw;
		min-height: 95vh;
		display: flex;
		align-items: center;
		justify-content: center;
		background: linear-gradient(
			90deg,
			rgba(252, 252, 252, 1) 0%,
			rgba(255, 249, 234, 1) 35%,
			rgba(236, 198, 238, 1) 100%
		);
	}
</style>
