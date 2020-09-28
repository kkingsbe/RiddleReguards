<script>
    export let id
    import Comment from "./Comment.svelte" 
    var comments = []

    async function getComments(id) {
        return new Promise((resolve, reject) => {
            var requestOptions = {
                method: 'POST',
                body: JSON.stringify({id: id}),
                redirect: 'follow'
            };

            fetch("https://jeow7risp7.execute-api.us-east-1.amazonaws.com/RRGetComments", requestOptions)
                .then(response => response.text())
                .then(result => {
                    screen = "posts"
                    resolve(JSON.parse(result))
                })
                .catch(error => {
                    console.log('error', error)
                    reject(error)
                });
        })
    }

    async function main() {
        console.log(id)
        comments = await getComments(id)
        console.log(comments)
    }

    main()
</script>

<main>
    {#if typeof(comments) == "object"}
        {#each comments as comment}
            <Comment timestamp={comment.timestamp} content={comment.text}></Comment>
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