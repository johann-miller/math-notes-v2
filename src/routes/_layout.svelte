<script>
	import Nav from '../components/Nav.svelte'
</script>

<style>
	.container {
		display: grid;
		grid-template-rows: 100vh;
		grid-template-columns: 16rem calc(100vw - 16rem);
	}

	main {
		display: flex;
		flex-flow: column;
		align-items: center;
		width: 100%;
		min-height: 100%;
	}
</style>

<div class="container">
	<Nav/>
	<main>
		<slot></slot>
	</main>
</div>