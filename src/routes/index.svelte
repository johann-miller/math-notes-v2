<script>
	
</script>

<style>
	header {
		display: flex;
		flex-flow: column;
		align-items: flex-start;
		padding: 0 2rem 1rem 2rem;
		border-bottom: 1px #d6d9dc solid;
		margin: 10rem 0 1rem 0;
	}

	h1 {
		margin-bottom: 1rem;
	}

	.large-screen-message {
		display: none;
	}

	.small-screen-message {
		padding: 0 2rem;
	}

	@media only screen and (min-width: 900px) {
		header {
			align-items: center;
		}

		.large-screen-message {
			display: inherit;
		}

		.small-screen-message {
			display: none;
		}
	}
</style>

<header>
	<h1>Johann Miller / Blog</h1>
	<p>A collection of posts to help you learn mathematics</p>
</header>


<p class="small-screen-message">Select a section by pressing "Menu" at the bottom left</p>
<p class="large-screen-message">Select a section from the left</p>