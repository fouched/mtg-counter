<script>
import './app.css'
import Team from './Team.svelte'

let winningText = ''
let winningColor = ''
let redScore = 20
let blueScore = 20

const onScoreSubmit = (e) => {
  const {score, color} = e.detail
  console.log('score:' + score + ' color:' + color)
  if (score === 0 ) {
    if (color.toUpperCase() === 'RED') {
      winningText = 'Red wins!'
      winningColor = 'text-red-500'
    } else if (color.toUpperCase() === 'BLUE') {
      winningText = 'Blue wins!'
      winningColor = 'text-blue-500'    
    }
  }
}

const resetGame = () => {
  winningText = ''
  redScore = 20
  blueScore = 20
  console.log('resetting game')
}

</script>

<div class="container mx-auto max-w-4xl">
  <div class="grid grid-cols-2 py-4">
    <div class="col-span-2 text-2xl font-bold mb-2 flex place-content-center">
      MTG Counter App
    </div>
    <Team color='red' bind:score={redScore} on:score_submit={onScoreSubmit}/>
    <Team color='blue' bind:score={blueScore} on:score_submit={onScoreSubmit}/>
    {#if winningText === ''}    
      <div class="col-span-2">
        <button on:click={resetGame} class="w-full bg-yellow-500 font-bold mt-3 p-1 rounded-md">Reset Game</button>
      </div>      
    {:else}
      <div class="flex place-content-center col-span-2 {winningColor} text-xl font-bold mt-2">
        {winningText}
      </div>    
      <div class="col-span-2">
        <button on:click={resetGame} class="w-full bg-green-800 text-white font-bold mt-3 p-1 rounded-md">New Game</button>
      </div>      
    {/if}
  </div>
</div>

