<template>
    <div class="container m-auto">
        <Timer/>
        <div class="computer flex flex-col items-center gap-3">
            <h1>Computer</h1>
            <div class="computer-action w-40 aspect-square border-2 border-dashed border-green-500 rounded text-center flex flex-col justify-center">
                {{ computerChoice }}
            </div>
            <p>
                Score: {{ updateComputerScore }}
            </p>
        </div>
        <div class="winner h-10 bg-green-500 rounded-full text-center my-6 flex flex-col justify-center">
            {{ winnerState }}
        </div>
        <div class="player flex flex-col items-center gap-3">
            <h1>Player</h1>
            <div class="player-action w-40 aspect-square border-2 border-dashed border-green-500 rounded text-center flex flex-col justify-center">
                {{ playerChoice }}
            </div>
            <p>
                Score: {{ updatePlayerScore }}
            </p>
        </div>
        <div class="buttons flex gap-16 justify-center mt-8">
            <button v-for="(item, index) in options" @click="makeChoice(index)" class="w-40 aspect-square border-2 border-dashed border-green-500 rounded bg-green-500 bg-opacity-80">
                {{ options[index] }}
            </button>
        </div>
    </div>
</template>

<script setup>
const options = ref(['rock', 'paper', 'scissor']);
let playerChoice = ref(null);
let computerChoice = ref(null);
let computerScore = ref(0)
let playerScore = ref(0)

const makeChoice = (index) => {
    playerChoice.value = options.value[index]
};
const updateComputerScore = computed(() => {
    if (winner.value === 'computer') {
        computerScore.value++
        winner.value = null
        return computerScore
    } else {
        return computerScore
    }
})
const updatePlayerScore = computed(() => {
    if (winner.value === 'player') {
        playerScore.value++
        return playerScore
    } else {
        return playerScore
    }
})
const winner = computed(() => {
    let winner = null
    if (playerChoice.value === 'rock' && computerChoice.value === 'paper') {
        winner = 'computer'
    } else if (playerChoice.value === 'scissor' && computerChoice.value === 'rock') {
        winner = 'computer'
    } else if (playerChoice.value === 'paper' && computerChoice.value === 'scissor') {
        winner = 'computer'
    } else {
        return winner
    }
    return winner
})
const winnerState = computed(() => {
    if(winner.value) {
        return `The winner is ${winner.value}!`
    }
})

watch(playerChoice, () => {
    if (playerChoice.value === 'rock') {
        computerChoice.value = 'paper'
    } else if (playerChoice.value === 'paper') {
        computerChoice.value = 'scissor'
    } else {
        computerChoice.value = 'rock'
    }
})
</script>
