<script lang="ts">
	import P5 from 'p5-svelte';
	import type p5 from 'p5';

	const sketch = (p5: p5) => {
		const length = 600;
		const stepSize = 10;
		const elementLength = length / stepSize;

		p5.setup = () => {
			p5.createCanvas(length, length);
			p5.noLoop();
			p5.background(0);
			p5.stroke(255);
		};

		p5.draw = () => {
			let shouldFill = false;

			for (let x = 0; x < stepSize; x++) {
				for (let y = 0; y < stepSize; y++) {
					p5.square(x * elementLength, y * elementLength, elementLength);

					shouldFill = Math.random() > 0.5;

					if (shouldFill) {
						p5.fill(255);
					} else {
						p5.fill(0);
					}
				}
			}
		};

		p5.keyPressed = () => {
			p5.redraw();
		};
	};
</script>

<figure>
	<P5 {sketch} />
	<figcaption class="mt-3 text-right text-gray-700 font-thin select-none">
		<h2>01. Pseudorandom Binary Grid</h2>
		<p class="text-xs italic">press any key to interact</p>
	</figcaption>
</figure>
