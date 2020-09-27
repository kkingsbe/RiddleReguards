<script>
	export let name;

	import Posts from "./components/Posts.svelte"
</script>

<main>
	<div class="title">
		<h1>Posts:</h1>
	</div>
	<Posts></Posts>
</main>

<style>
	main {
		text-align: center;
		width: 100%;
		height: 100%;
	}

	.title {
		padding: 1em 0 1em 0;
		width: 100%;
		background: whitesmoke;
		box-shadow: 3px 3px 5px 3px rgba(0,0,0,0.3);
		position: fixed;
	}

	h1 {
		font-size: 8vw;
		font-weight: 100;
		padding: 0px;
		margin: 0px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>