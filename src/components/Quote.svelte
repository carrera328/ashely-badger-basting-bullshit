<script>
    export let quote;
</script>

<main>
    <div class="content">
        {quote}
    </div>
</main>

<style>
    main {
        width: 100%;
        box-sizing: border-box;
        display: flex;
        flex-direction: row;
        justify-content: center;
        align-items: center;
    }
    .content {
        padding: 1%;
        box-sizing: border-box;
        overflow: scroll;
        word-break: break-word;
        font-size: .865em;
        width: 100%;
        text-align: center;
        max-height: 300px;
    }
</style>
