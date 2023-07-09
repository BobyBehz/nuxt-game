<template>
    <div class="default-nav">
        <ul class="flex justify-center bg-green-500 rounded py-2 gap-2 items-center">
            <li class=" cursor-pointer">
                <NuxtLink to="/">Home</NuxtLink>
            </li>
            |
            <li class=" cursor-pointer">
                <NuxtLink to="/RockPaperScissor">Rock, Paper, Scissor</NuxtLink>
            </li>
        </ul>
    </div>
    <slot/>
</template>

<script setup>

</script>

<style scoped>

</style>