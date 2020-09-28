<script>
    import Post from "./Post.svelte"
    export let select

    var posts = []
    
    async function main() {
        posts = await getPosts()
        console.log(posts)
    }

    async function getPosts() {
        return new Promise((resolve, reject) => {
            fetch("https://jeow7risp7.execute-api.us-east-1.amazonaws.com/RRGetPosts")
            .then(res => {
                return res.json()
            })
            .then(data => {
                posts = data
                resolve(posts)
            })
        })
    }

    main()
</script>

<main>
    {#if typeof(posts) == "object"}
        {#each posts as post}
            <Post id={post.id} content={post.text} select={select}></Post>
        {/each}
    {/if}
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 7em;
    }
</style>