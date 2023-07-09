<template>
    <div class="welcome container m-auto text-center mt-7 flex flex-wrap justify-center">
        <h1 class="basis-full">Welcome</h1>
        <p class="text-green-500 basis-full">Chose your game</p>
        <ul class="flex justify-center bg-green-500 rounded py-2 gap-2 items-center w-1/2 basis-1/2 mt-5">
            <li class=" cursor-pointer">
                <NuxtLink to="/RockPaperScissor">Rock, Paper, Scissor</NuxtLink>
            </li>
        </ul>
    </div>
</template>

<script setup>

</script>

<style scoped>
.welcome h1 {
    font-size: 80px;
}
.welcome p {
    font-size: 40px;
}
</style>