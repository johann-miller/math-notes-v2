<script>
	import Nav from '../components/Nav.svelte'
</script>

<style>
	main {
		display: flex;
		flex-flow: column;
		align-items: center;
		width: 100vw;
	}
</style>

<Nav />

<main>
	<slot></slot>
</main>