<script>
    let root;
    let ashleyInput;

    const handleKeyUp = (event) => {
        if (event.keyCode === 13) {
            handleClick();
            return;
        }

        ashleyInput = event.target.value;
    }

    const handleClick = () => {
        let aiPrompt;


        if (!ashleyInput) {
            alert('Type in what you wanna learn about');
            return;
        }

        aiPrompt = `Tell me a fun fact about ${ashleyInput}`;

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
    <input on:keyup={handleKeyUp} type='text' data-id="ashley-input" placeholder="I want to learn about..."/>
    <button on:click={handleClick} data-id="server">Get me some mfing knowledge cuzzo</button>
</main>

<style>
    main {
        display: flex;
        flex-direction: column;
        align-items: center;  
    }

    input {
        width: 100%;
    }

    button {
        width: 50%;
        font-size: .75em;
    }
</style>
