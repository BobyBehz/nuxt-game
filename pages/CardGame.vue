<template>
    <div class="container m-auto">
        <div v-if="gameOver">
            You Won!!!!
        </div>
        <ul :class="['flex flex-wrap mt-10', temporaryPause ? 'pointer-events-auto' : 'pointer-events-none']">
            <li v-for="card in cards" :key="card.id" class="basis-1/4 p-3">
                <div @click="flipCard(card)" :class="['h-[400px] rounded-2xl cursor-pointer', card.turned ? `bg-${card.color}-500` : 'bg-gray-500']">

                </div>
            </li>
        </ul>
    </div>
</template>

<script setup>
const cards = ref([
    {
        color: 'red',
        id: 1,
        turned: false
    },
    {
        color: 'green',
        id: 2,
        turned: false
    },
    {
        color: 'red',
        id: 3,
        turned: false
    },
    {
        color: 'blue',
        id: 4,
        turned: false
    },
    {
        color: 'green',
        id: 5,
        turned: false
    },
    {
        color: 'blue',
        id: 6,
        turned: false
    },
    // {
    //     color: 'pink',
    //     id: 7,
    //     turned: false
    // },
    // {
    //     color: 'pink',
    //     id: 8,
    //     turned: false
    // },
])
const clickedCards = ref([])

const flipCard = (card) => {
    card.turned = true
    if (clickedCards.value.length < 1) {
        clickedCards.value.push(card)
    } else {
        console.log(clickedCards.value[0].color)
        clickedCards.value.push(card)
        setTimeout(() => {
            if (clickedCards.value[0].color != clickedCards.value[1].color) {
                cards.value.forEach((card) => {
                    if (card.id === clickedCards.value[0].id || card.id === clickedCards.value[1].id) {
                        card.turned = false
                    }
                })            
            }
            clickedCards.value = []
        }, 500)
    }
    console.log(clickedCards.value)
}

const temporaryPause = computed(() => {
    let play = true
    if (clickedCards.value.length >= 2) {
        play = false
    }
    return play
})
const gameOver = computed(() => {
    let over = cards.value.every((card) => {card.turned === true})
    return over
})
console.log()
</script>
