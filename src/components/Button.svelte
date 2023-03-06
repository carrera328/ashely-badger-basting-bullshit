<script>
    let root;
    const handleClick = (event) => {
        let aiPrompt;

        switch (event.target.dataset.id) {
            case "interest":
                aiPrompt = "Tell me a cool fun fact";
                break;
            case "wisdom":
                aiPrompt = "Get me some eastern wisdom";
                break;
            case "love":
                aiPrompt = 'Get me a love quote for an adventerous, curious, beautiful woman'
                break;
            case "laugh":
                aiPrompt = "Tell me a witty joke"
            default:
            // do nothing
        }

        root.dispatchEvent(
            new CustomEvent("quoteclick", {
                detail: aiPrompt,
                bubbles: true,
                composed: true,
            })
        );
    };
</script>

<main bind:this={root}>
    <button on:click={handleClick} data-id="laugh">Tell Me A Joke</button>
    <button on:click={handleClick} data-id="interest">Fun Fact Generator</button>
    <button on:click={handleClick} data-id="love">Tell Me Somthing Mushy</button>
    <button on:click={handleClick} data-id="wisdom">Where is my Sage?</button>
</main>

<style>
    main {
        display: grid;
        grid-template-columns: 1fr 1fr;
        grid-template-rows: 1fr 1fr;
        background-color: none;
        
    }

    button {
        height: 100%;
        width: 100%;
        font-family: inherit;
        font-size: .5em;
        background-color: #97ac9d;
        color: white;
    }
</style>
