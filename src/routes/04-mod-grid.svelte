<script lang="ts">
	import P5 from 'p5-svelte';
	import type p5 from 'p5';

	let brainfuck = true;

	const sketch = (p5: p5) => {
		let time = 0.05;
		let stepSize = 10;
		const length = 600;
		const elementLength = length / stepSize;

		p5.setup = () => {
			p5.createCanvas(length, length);
			p5.background(0);
			p5.stroke(255);
		};

		p5.draw = () => {
			let shouldFill = false;

			for (let x = 0; x < stepSize; x++) {
				for (let y = 0; y < stepSize; y++) {
					p5.square(x * elementLength, y * elementLength, elementLength);

					if (brainfuck) {
						shouldFill = (x - y) % 3 > Math.round(Math.tan(time) * 4);
					} else {
						shouldFill =
							(y % 2 === Math.round(Math.cos(time) ** 2) &&
								x % 1 === Math.round(Math.sin(time) ** 2)) ||
							Math.sin(time / 4 - x + 2 * y) > 0.5;
					}

					if (shouldFill) {
						p5.fill(255);
					} else {
						p5.fill(0);
					}
				}
			}
			time += 0.125;
		};
	};
</script>

<figure>
	<label for="brainfuck">Brain</label>
	<input type="radio" name="brainfuck" id="brainfuck" bind:group={brainfuck} value={true} />
	<label for="brainfuck">Boil</label>
	<input type="radio" name="simmer" id="simmer" bind:group={brainfuck} value={false} />
	<P5 {sketch} />
	<figcaption class="mt-3 text-right text-gray-700 font-thin select-none">
		<h2>04. Mod Grid</h2>
	</figcaption>
</figure>
