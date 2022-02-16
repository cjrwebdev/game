<script>
    let numQuestions
    let num1 = Math.floor(Math.random() * 12)
    let num2 = Math.floor(Math.random() * 12)
    let product = num1 * num2
    let numInput = 5
    let ansInput = ''
    let answer = 0
    let isShown = false
    let correct = 0
    let isDisabled = false
    const handleClick = () => {
        numQuestions = numInput
    }  
    
    const handleAnsClick = () => {
        answer = ansInput
        isShown = !isShown
        isDisabled = true
        if(answer == product) {
            correct += 1
        }
        
    }
    
    const handleNext = () => {
        numQuestions -= 1
        num1 = Math.floor(Math.random() * 12)
        num2 = Math.floor(Math.random() * 12)
        product = num1 * num2
        answer = ansInput
        isShown = !isShown
        isDisabled = false
        ansInput = ''
    }
    
    const handlePlayAgain = () => {
        window.location.href=window.location.href
    }
    </script>
    
    <div class="game-board">
        {#if numQuestions === undefined}
        <h2 class="question" for="num-questions">How many questions do you want?</h2>
        <!-- svelte-ignore a11y-autofocus -->
        <input type="text" bind:value = {numInput}  autofocus>
        <br>
        <button type="submit" on:click={handleClick}>Submit</button>
        {/if}
        {#if numQuestions > 0}
            <h2 class="equation">{num1} x {num2} = {ansInput} </h2>
            <!-- svelte-ignore a11y-autofocus -->
            <input type="text" bind:value = {ansInput}  autofocus>
            <br>
            <button on:click={handleAnsClick} disabled={isDisabled}>Check</button>
        {/if}
        {#if isShown && answer == product}
                <h2 class="right-ans">You are correct!</h2>
                <button on:click={handleNext}>Next question</button>
            {:else if isShown && answer != product}         
                <h2 class="wrong-ans">Sorry the correct answer is {product}</h2>
                <button on:click={handleNext}>Next</button>
        {/if}
        {#if numQuestions == 0}
            <h2 class="score">You got {correct} out of {numInput} right that is an {correct / numInput * 100}%</h2>
            <button on:click={handlePlayAgain}>Play Again?</button>
        {/if}
        
    </div>
    
    <style>
        .game-board {
            text-align: center;
            font-family: 'Rubik', sans-serif;
        }
    
        .question {
            color: yellow;
        }
    
        .right-ans {
            color: lime;
            font-size: 2rem;
            margin-top: 0;
        }
    
        .equation {
            color: rgb(145, 255, 0);
            font-size: 2rem;
        }
    
        .wrong-ans {
            color: red;
            font-size: 1.5rem;
            margin-top: 0;
        }
    
        input {
            margin-bottom: 1.5em;
        }
    
        button {
            padding: .5em 2em;
            font-family: 'Rubik', sans-serif;
            font-weight: bold;
            background: rgb(1, 183, 255);
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
    
        button:hover {
            background: aqua;
        }
    
        button:disabled {
            display: none;
        }
    
        .score {
            color: yellow;
            
        }
    
        @media (min-width: 800px) {
            .question {
                font-size: 2.5rem;
                margin-top: 0;
            }
    
            .equation {
                font-size: 3rem;
            }
    
            button {
                padding: 1em 2em;
            }
    
            input {
                height: 30px;
                margin-bottom: 1em;
                font-weight: bold;
                text-align: center;
                font-size: 1.5rem;
                width: 50%;
            }
    
            .score {
                font-size: 2rem;
            }
    
            .wrong-ans {
                font-size: 1.75rem;
            }
        }
    </style>