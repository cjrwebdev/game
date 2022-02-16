<script>
    export let add
    export let multi
</script>
<div class="choose-container">
    <h2 class="question">Which Mode would you like to play?</h2>
    <div class="button-container">   
        <button class="add" on:click={add}>Add</button>
        <button class="multi" on:click={multi}>Multiply</button>
    </div>      
    
</div>

<style>
    .choose-container {
        text-align: center;
    }

    .question {
        font-family: 'Rubik', sans-serif;
        color: yellow;
    }

    .button-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 1em;
        
    }

    button{
        height: 100px;
        width: 50%;
        font-family: sans-serif;
        font-size: 2rem;
        border-radius: 10px;
        margin-bottom: 1em;
    }

    .add {
        background: green;
        cursor: pointer;
    }

    .add:hover {
        background: lime;
    }

    .multi {
        background: orange;
        cursor: pointer;
    }

    .multi:hover {
        background: yellow;
    }

</style>