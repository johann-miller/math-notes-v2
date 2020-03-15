<script>
	import Nav from '../components/Nav.svelte'
</script>

<style>
	.container {
		display: grid;
		grid-template-rows: 100vh;
		grid-template-columns: 15rem calc(100vw - 15rem);
	}

	main {
		display: flex;
		flex-flow: column;
		align-items: center;
		width: 100%;
		height: 100%;
		overflow-y: scroll;
	}
</style>

<div class="container">
	<Nav/>
	<main>
		<slot></slot>
	</main>
</div>