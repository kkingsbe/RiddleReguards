<script>
    export let screen
    export let id
    
    var addingComment = false
    var text = ""
    async function addComment() {
        if(!addingComment) {
            addingComment = true
            return new Promise((resolve, reject) => {
                var requestOptions = {
                    method: 'POST',
                    body: JSON.stringify({id: id, text: text}),
                    redirect: 'follow'
                };

                fetch("https://jeow7risp7.execute-api.us-east-1.amazonaws.com/RRaddComment", requestOptions)
                    .then(response => response.text())
                    .then(result => {
                        console.log(result)
                        screen = "viewcomments"
                        addingComment = false
                        resolve(result)
                    })
                    .catch(error => {
                        console.log('error', error)
                        addingComment = false
                        reject(error)
                    });
            })
        }
    }
</script>

<main>
    <textarea class="postEntry" bind:value={text}></textarea>
    <div class="submit" on:click={addComment}><p>Submit</p></div>
</main>

<style>
    main {
        height: 100vh;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }

    .postEntry {
        width: 75vw;
        height: 30vh;
        border-radius: 20px;
        text-align: start;
        resize: none;
        font-size: 5vw;
    }

    .postEntry:focus {
        outline: none;
    }

    .submit {
        background: #FFF895;
        padding: 30px;
        border-radius: 20px;
        padding: 10px 20px 10px 20px;
        margin-top: 15px;
		box-shadow: 2px 2px 5px 2px rgba(0,0,0,0.2);
    }

    .submit p {
        font-size: 7vw;
        padding: 0;
        margin: 0;
    }

    @media (min-width: 100vh) {
		.submit p {
            font-size: 5vh;
        }

        .postEntry {
            width: 75vh;
            height: 30vh;
        }
	}
</style>