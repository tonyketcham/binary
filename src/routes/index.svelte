<script lang="ts">
	const posts = [
		{
			title: '01. Pseudorandom Grid',
			route: '/01-pseudorandom-grid'
		},
		{
			title: '02. Perlin Grid',
			route: '/02-perlin-grid'
		}
	];
</script>

<nav>
	<ul>
		{#each posts as post}
			<li>
				<a href={post.route} sveltekit:prefetch>
					{post.title}
				</a>
			</li>
		{/each}
	</ul>
</nav>
