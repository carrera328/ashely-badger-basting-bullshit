<!-- trip planner -->
<script>
    import {onMount} from "svelte";
    import Button from "./components/Button.svelte";
    import Quote from "./components/Quote.svelte";
    import {DoubleBounce} from "svelte-loading-spinners";

    let root;
    let quote = 'Reach for the stars...';
    let loading = false;

    onMount(async () => {
        addEventListeners();
    });

    const addEventListeners = () => {
        root.addEventListener("quoteclick", async (event) => {
            loading = true;
            await handleQuoteClick(event);
            loading = false;
        });
    };

    const handleQuoteClick = async (event) => {
        quote = await getAI(event.detail);
        console.log("stuff", quote);
    };

    const getAI = async (prompt) => {
        const res = await fetch("https://gpt-3-mid.herokuapp.com/", {
            method: "POST",
            headers: {"Content-Type": "application/json"},
            body: JSON.stringify({prompt: prompt}),
        }).then((data) => data.text());

        return res;
    };
</script>

<main class="container" bind:this={root}>
    <h1 class="title">Weed Gets Ashley High</h1>
	

    <div class="quote">
        {#if loading}
            <DoubleBounce size="5" color="#e6a484" unit="rem" duration="1s" />
        {:else}
            <Quote {quote} />
        {/if}
    </div>
    <div class="button">
        <Button />
    </div>
</main>

<style>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        background-color: #325a5c;
        height: 100vh;
        padding: 2%;
		width: 100%;
		box-sizing: border-box;
    }

    .title {
        text-align: center;
		color: #e6a484
    }

    .quote {
        background-color: #97ac9d;
        border-radius: 2.5%;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		min-height: 200px;
        max-height: 200px;
        overflow: auto;
		word-break: break-word;
		width: 100%;
		box-sizing: border-box;
		color: white;
		
    }

    .button {
        margin-bottom: 20%;
    }
</style>
