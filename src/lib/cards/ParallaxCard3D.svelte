<script lang="ts">
	//   var o = $(".card");
	// $("#top").on("mousemove", function (t) {
	//     var e = -($(window).innerWidth() / 2 - t.pageX) / 30,
	//         n = ($(window).innerHeight() / 2 - t.pageY) / 10;
	//     o.attr("style", "transform: rotateY(" + e + "deg) rotateX(" + n + "deg);-webkit-transform: rotateY(" + e + "deg) rotateX(" + n + "deg);-moz-transform: rotateY(" + e + "deg) rotateX(" + n + "deg)")
	// })

	let a = 0;
	let b = 0;
	let c = 0;

	let element: HTMLDivElement;
	$: {
		console.log(b);
	}
</script>

<div
	class="perspective"
	bind:this={element}
	on:mousemove={(e) => {
		const rect = element.getBoundingClientRect();

		a = -(e.offsetX - rect.width / 2) / 10;
		b = (e.offsetY - rect.height / 2) / 20;
	}}
>
	<div class="card" style={`transform: rotateY(${a}deg) rotateX(${b}deg) rotateZ(${c}deg);`}>
		<h1>Test</h1>
	</div>
</div>

<style lang="scss">
	.perspective {
		transition: transform 0.15s cubic-bezier(0.25, 0.46, 0.45, 0.94);
		perspective: 500px;
		&:hover {
			transform: scale(1.3);
		}
	}
	.card {
		width: 270px;
		height: 413px;
		display: flex;
		flex-direction: column;
		align-items: center;

		box-shadow: 0 70px 63px -60px #494848;
		transform-style: preserve-3d;
		transition: transform 0.05s linear;

		border: 1px solid grey;

		.thumb {
			background-size: cover;
			height: 100%;
			width: 100%;
			border-radius: 15px;

			&:after {
				background: inherit;
				content: '';
				display: block;
				position: absolute;
				left: -60px;
				top: 40px;
				width: 100%;
				height: 108%;
				z-index: -1;
				filter: blur(55px);
			}
		}

		h1 {
			font-size: 40px;
			font-weight: 100;
			transform: translateZ(30px);
		}

		span {
			position: absolute;
			bottom: 40px;
			right: -280px;
			font-size: 37px;
			font-weight: 600;
			transform: translateZ(35px);
		}
	}

	img {
		margin: auto;
		display: block;
		border-radius: 15px;
	}
</style>
