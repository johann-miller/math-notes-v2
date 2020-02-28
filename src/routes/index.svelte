<script>
	let subjects = [
		{
			title: "Subject 1",
			image: "https://via.placeholder.com/200x80"
		},
	]
</script>

<style>
	header {
		display: flex;
		flex-flow: column;
		align-items: center;
		padding: 0 2rem 1rem 2rem;
		border-bottom: 1px #d6d9dc solid;
		margin-bottom: 1rem;
	}

	.subjects {
		display: flex;
		flex-flow: column;
		list-style-type: none;
	}

	.subject {
		border: 1px #d6d9dc solid;
		margin-bottom: 1.5rem;
		width: 20rem;
		max-width: 100%;
	}
</style>

<header>
	<h1>Johann Miller / Blog</h1>
	<p>A collection of my posts to help you learn mathematics</p>
</header>

<ul class="subjects">
	{#each subjects as subject}
		<li class="subject">
			<img src="{subject.image}" alt="subject-image">
			<h2 class="subject-title">{subject.title}</h2>
		</li>
	{/each}
</ul>