<template>
    <div>
        <div class="time text-center my-5 w-12 m-auto bg-green-500 rounded cursor-pointer">
            {{ updateTimer }}
        </div>
        <div class="flex justify-center gap-5 mb-8">
            <div v-if="timeState === 'begin'" @click="startTime" class="time text-center w-14 bg-green-500 rounded cursor-pointer">
                start
            </div>
            <div v-if="timeState === 'running'" @click="pauseTime" class="time text-center w-14 bg-green-500 rounded cursor-pointer">
                pause
            </div>
            <div v-if="timeState === 'stopped'" @click="startTime" class="time text-center w-14 bg-green-500 rounded cursor-pointer">
                resume
            </div>
            <div v-if="timeState !== 'begin'" @click="reset" class="time text-center w-14 bg-green-500 rounded cursor-pointer">
                reset
            </div>
        </div>
    </div>
</template>

<script setup>
let time = ref(0)
let interval = ref(null)
let timeState = ref('begin')

const startTime = () => {
    timeState.value = 'running'
    interval.value = setInterval(() => {
        time.value++
    }, 1000);
}
const pauseTime = () => {
    timeState.value = 'stopped'
    clearInterval(interval.value)
    interval.value = null
}
const reset = () => {
    timeState.value = 'begin'
    clearInterval(interval.value)
    time.value = 0
}
const updateTimer = computed(() => {
    let minutes = Math.floor(time.value / 60)
    let seconds = time.value % 60
    if (minutes < 10) {
        minutes = '0' + minutes
    }
    if (seconds < 10) {
        seconds = '0' + seconds
    }
    return `${minutes} : ${seconds}`
})
const starOnMount = onMounted(() => {
    timeState.value = 'running'
    interval.value = setInterval(() => {
        time.value++
    }, 1000);
})
</script>
