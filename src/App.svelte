<script>

    import Multi from "./Multi.svelte";
    import Header from "./Header.svelte";
    import Choose from "./Choose.svelte";
    import Add from "./Add.svelte";
    
    let mode = undefined
    const multi = () => {
    mode = 'multi'
}

const add = () => {
    mode = 'add'
}
</script>

    <div class="game-container">
        <Header />
        {#if mode === undefined}
        <Choose
            {add}
            {multi}
            
        />
            
        {/if}
        {#if mode === 'multi'}
        <Multi />
        {/if}
        {#if mode === 'add'}
        <Add />
        {/if}

    </div>
    <p>Photo by <a href="https://unsplash.com/@dana_luig?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Dana Luig</a> on <a href="https://unsplash.com/s/photos/stars?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
    </p>

<style>
    
    .game-container {
        background: rgba(9, 1, 39, 0.7);
        margin: 20vh auto;
        height: 70vh;
        width: 40vw;
        min-width: 300px;
        border-radius: 10px;
    }

    p {
        position: absolute;
        bottom: 1px;
        font-size: 12px;
        background-color: rgb(250, 235, 215, .5);
        padding: 5px 10px;
        border-radius: 0 10px 10px 0;
    }

    a {
        text-decoration: none;
        font-family: 'Rubik', sans-serif;
    }
</style>