<script lang="ts">
	import P5 from 'p5-svelte';
	import type p5 from 'p5';

	const sketch = (p5: p5) => {
		let time = 0.05;
		let stepSize = 10;
		const length = 600;
		const elementLength = length / stepSize;

		let noiseVal;
		let noiseScale = 1;

		p5.setup = () => {
			p5.createCanvas(length, length);
			p5.background(0);
			p5.stroke(255);
		};

		p5.draw = () => {
			let shouldFill = false;

			for (let x = -1; x < stepSize; x++) {
				for (let y = -1; y < stepSize; y++) {
					p5.square(x * elementLength, y * elementLength, elementLength);
					noiseVal = p5.noise(x * noiseScale + time, y * noiseScale + time);

					shouldFill = noiseVal > 0.5;

					if (shouldFill) {
						p5.fill(255);
					} else {
						p5.fill(0);
					}
				}
			}
			time += 0.01;
		};
	};
</script>

<figure>
	<P5 {sketch} />
	<figcaption class="mt-3 text-right text-gray-700 font-thin select-none">
		<h2>02. Perlin Grid</h2>
	</figcaption>
</figure>
