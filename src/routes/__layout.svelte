<script>
	import '../app.css';
</script>

<svelte:head>
	<title>Binary Systems</title>
</svelte:head>

<div class="relative h-screen">
	<header class="absolute inset-0 bottom-auto p-1 flex space-x-1">
		<span
			aria-hidden="true"
			role="presentation"
			class="inline-block w-1 h-1 bg-white border border-black my-auto"
		/>
		<h1 class="my-auto h-full"><a sveltekit:prefetch href="/">Binary</a></h1>
	</header>
	<main class="grid place-items-center h-full">
		<slot />
	</main>
</div>
