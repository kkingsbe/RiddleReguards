<script>
    export let id
    export let content
    export let select
    export let comments

    import cssVars from 'svelte-css-vars'
    var numComments = 0

    async function main() {
        numComments = (await getComments(id)).length
    }

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

    main()

    var hue = id * 13
    $: vars = {
        hue: hue
    }
</script>

<main use:cssVars={vars} on:click={select(id)}>
    <h1>#{id}</h1>
    <p>{content}</p>
    <p class="num-comments">{numComments} comments</p>
</main>

<style>
    main {
        background: hsl(var(--hue), 100%, 87%);
        border-radius: 20px;
        width: 80vw;
        margin-bottom: 20px;
        box-shadow: 3px 3px 5px 3px rgba(0,0,0,0.2);
        padding: 10px;
        font-size: 1.2em;
    }

    h1 {
		font-size: 6vw;
		font-weight: 100;
		padding: 0px;
        margin: 0px;
        text-align: start;
        padding: 5px 0 15px 5px;
    }
    
    p {
        padding: 0;
        margin: 0;
    }

    .num-comments {
        width: 100%;
        text-align: start;
        font-size: 13px;
        margin-top: 20px;
    }
</style>