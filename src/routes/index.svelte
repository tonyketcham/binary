<script lang="ts">
	const posts = [
		{
			title: '01. Pseudorandom Binary Grid',
			route: '/01-pseudorandom-binary-grid'
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
