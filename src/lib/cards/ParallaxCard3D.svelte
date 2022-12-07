<script lang="ts">
	let hori = 0;
	let vert = 0;

	let deadzone = 0.17;
	let angle = 10;

	let element: HTMLElement;
	$: {
	}
</script>

<div
	class="perspective"
	bind:this={element}
	on:mousemove={(e) => {
		const rect = element.getBoundingClientRect();

		vert =
			(Math.min(Math.max((e.pageY - rect.top) / rect.height, deadzone), 1 - deadzone) - 0.5) *
			(1 / (1 - deadzone * 2)) *
			angle;

		hori =
			-(Math.min(Math.max((e.pageX - rect.left) / rect.width, deadzone), 1 - deadzone) - 0.5) *
			(1 / (1 - deadzone * 2)) *
			angle;
	}}
>
	<div class="card" style={`transform: rotateY(${hori}deg) rotateX(${vert}deg);`}>
		<img
			src="https://emshop.pl/pol_pm_LEGO-Star-Wars-Gwiezdne-wojny-Mandalorianin-i-the-child-baby-Yoda-75317-4648_4.jpg"
			alt="baby yoda toy"
			class="product-img"
		/>
		<span class="product-title"
			>LEGO Star Wars Gwiezdne wojny Mandalorianin i the child baby Yoda 75317</span
		>
	</div>
</div>

<style lang="scss">
	.product-img {
		width: 100%;
	}

	.perspective {
		transition: transform 0.15s cubic-bezier(0.25, 0.46, 0.45, 0.94);
		perspective: 500px;
		&:hover {
			transform: scale(1.3);
			.product-title {
				transform: translateZ(35px);
			}
		}
	}
	.card {
		width: 200px;
		height: 313px;
		padding: 1.5rem 0.75rem;
		display: flex;
		flex-direction: column;
		align-items: center;

		box-shadow: 0 70px 63px -60px #8d4689;
		transform-style: preserve-3d;
		transition: transform 0.05s linear;
		background-color: white;

		// border: 1px solid grey;
	}
</style>
