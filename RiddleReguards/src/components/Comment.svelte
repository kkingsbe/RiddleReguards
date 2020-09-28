<script>
    export let timestamp
    export let content
    export let select

    var date = new Date(timestamp)
    console.log(date)
    var hours = date.getHours() < 10 ? "0" + date.getHours() : date.getHours()
    var minutes = date.getMinutes() < 10 ? "0" + date.getMinutes() : date.getMinutes()
    var time = `${hours}:${minutes}`
</script>

<main>
    <h1>{time}</h1>
    <p>{content}</p>
</main>

<style>
    main {
        background: hsl(50, 69%, 85%);
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