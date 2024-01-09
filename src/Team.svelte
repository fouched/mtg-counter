<script>
export let color
export let score
export let gameOver

let borderColor = ''
let fontColor = ''
let teamText = ''

if (color.toUpperCase() === 'RED') {
	borderColor = 'border-red-500'
	fontColor = 'text-red-500'
	teamText = 'Red'
} else {
	borderColor = 'border-blue-500'
	fontColor = 'text-blue-500'
	teamText = 'Blue'
}

const increaseScore = () => {
	if (score >= 0 && score < 20) {
		score++
	}
}

const decreaseScore = () => {
	if (score > 0 && score <= 20) {
		score--
	}
}

</script>
<div>
	<div class="border-4 {borderColor} border-dashed mr-1">
		<div class="text-xl font-bold {fontColor} mt-3 flex place-content-center">Team {teamText}: {score}</div>
		<div class="mb-3 flex place-content-center">
			<div><button disabled={gameOver} on:click={increaseScore} class="bg-green-500 w-8 h-8 mr-1 rounded-md font-extrabold text-white">+</button></div>
			<div><button disabled={gameOver} on:click={decreaseScore} class="bg-red-500 w-8 h-8 rounded-md font-extrabold text-white">-</button></div>
		</div>        
	</div>      
</div>