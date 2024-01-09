<script>
import './app.css'
import Team from './Team.svelte'

let winningText = ''
let winningColor = ''
let redScore = 20
let blueScore = 20

$: redWon = blueScore === 0
$: blueWon = redScore === 0
$: gameOver = redWon || blueWon

$: if (redWon) {
    winningText = 'Red wins!'
    winningColor = 'text-red-500'
} else {
    winningText = 'Blue wins!'
    winningColor = 'text-blue-500'    
}

const resetGame = () => {
  winningText = ''
  redScore = 20
  blueScore = 20
}

</script>

<div class="container mx-auto max-w-4xl">
  <div class="grid grid-cols-2 py-4">
    <div class="col-span-2 text-2xl font-bold mb-2 flex place-content-center">
      MTG Counter App
    </div>
    <Team {gameOver} color='red' bind:score={redScore} />
    <Team {gameOver} color='blue' bind:score={blueScore} />
    {#if gameOver}  
      <div class="flex place-content-center col-span-2 {winningColor} text-xl font-bold mt-2">
        {winningText}
      </div>    
      <div class="col-span-2">
        <button on:click={resetGame} class="w-full bg-green-800 text-white font-bold mt-3 p-1 rounded-md">New Game</button>
      </div>            
    {:else}
      <div class="col-span-2">
        <button on:click={resetGame} class="w-full bg-yellow-500 font-bold mt-3 p-1 rounded-md">Reset Game</button>
      </div>      
    {/if}
  </div>
</div>

