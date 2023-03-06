<script>
    let root;
    const handleClick = (event) => {
        let aiPrompt;

        switch (event.target.dataset.id) {
            case "interest":
                aiPrompt = "Tell me an obscure fact";
                break;
            case "mike":
                aiPrompt = "Tell me a joke on people named Michael";
                break;
            case "server":
                aiPrompt = 'Get me fun facts about servers/waitresses or a joke about waiters or servers';
                break;
            case "ashley":
                aiPrompt = "Tell me a fun fact about famous people named ashley throughout history"
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
    <button on:click={handleClick} data-id="mike">Dicking on Mikes</button>
    <button on:click={handleClick} data-id="interest">Fun Fact Generator</button>
    <button on:click={handleClick} data-id="ashley">Famous Ashley's Through History</button>
    <button on:click={handleClick} data-id="server">A Server's Life</button>
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
