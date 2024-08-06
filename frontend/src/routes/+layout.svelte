<script>
	import Header from './Header.svelte';
</script>

<nav>
	<Header></Header>
</nav>

<slot></slot>

<style lang="postcss">
	:global(body) {
		@apply bg-white dark:bg-gray-800;
	}
</style>