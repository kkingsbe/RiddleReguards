<script>
    export let id
    export let content
    import cssVars from 'svelte-css-vars'

    var hue = id * 13
    console.log(hue)
    $: vars = {
        hue: hue
    }
</script>

<main use:cssVars={vars}>
    <h1>#{id}</h1>
    <p>{content}</p>
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
</style>