<script>
	export let name;
	import Posts from "./components/Posts.svelte"
	import NewPost from "./components/NewPost.svelte"
	import ViewComments from "./components/ViewComments.svelte"
	import NewComment from "./components/NewComment.svelte"

	var selectedId
	let screen = "posts"
	function newpost() {
		screen = "newpost"
	}
	function viewComments(id) {
		selectedId = id
		screen = "viewcomments"
	}
	function newcomment() {
		screen = "newcomment"
	}
</script>

<main>
	{#if screen == "posts"}
		<div class="title">
			<h1>Posts:</h1>
		</div>
		<Posts select={viewComments} selectedId={selectedId}></Posts>
		<div class="newPost" on:click={newpost}><p>+</p></div>
	{/if}
	{#if screen == "newpost"}
		<div class="title">
			<h1>New Post</h1>
		</div>
		<NewPost bind:screen={screen}></NewPost>
	{/if}
	{#if screen == "viewcomments"}
		<div class="title">
			<h1>Comments</h1>
		</div>
		<ViewComments id={selectedId} bind:screen={screen}></ViewComments>
		<div class="newPost" on:click={newcomment}><p>+</p></div>
	{/if}
	{#if screen == "newcomment"}
		<div class="title">
			<h1>New Comment</h1>
		</div>
		<NewComment id={selectedId} bind:screen={screen}></NewComment>
	{/if}
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
		top: 0;
	}

	h1 {
		font-size: 8vw;
		font-weight: 100;
		padding: 0px;
		margin: 0px;
	}

	.newPost {
		border-radius: 50%;
		width: 3.5em;
		height: 3.5em;
		background: rgb(238, 157, 157);
		color: white;
		box-shadow: 2px 2px 5px 2px rgba(0,0,0,0.2);
		display: flex;
		align-items: center;
		justify-content: center;
		position: fixed;
		right: 25px;
		bottom: 25px;
		cursor: pointer;
	}

	.newPost p {
		font-size: 3em;
		padding: none;
		margin: none;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>