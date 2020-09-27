<script>
    import Post from "./Post.svelte"
    var posts = []
    
    async function main() {
        posts = await getPosts()
        console.log(posts)
    }
    async function getPosts() {
        return new Promise((resolve, reject) => {
            resolve([{id: 1, text: "Frogs are gay"}, {id: 2, text: "Chemtrails Suck"}, {id: 3, text: "We hold these truths to be self-evident, that all men are created equal, that they are endowed by their Creator with certain unalienable Rights, that among these are Life, Liberty and the pursuit of Happiness.--That to secure these rights, Governments are instituted among Men, deriving their just powers from the consent of the governed, --That whenever any Form of Government becomes destructive of these ends, it is the Right of the People to alter or to abolish it, and to institute new Government, laying its foundation on such principles and organizing its powers in such form, as to them shall seem most likely to effect their Safety and Happiness. Prudence, indeed, will dictate that Governments long established should not be changed for light and transient causes"}, {id: 4, text: "Test 4"}])
        })
    }

    main()
</script>

<main>
    {#each posts as post}
        <Post id={post.id} content={post.text}></Post>
    {/each}
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 7em;
    }
</style>