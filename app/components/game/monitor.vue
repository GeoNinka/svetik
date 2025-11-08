<template>
    <div class="monitor">
        <p>{{ gameStore.questionIndex }} / 8</p>
        <Questions1 v-if="gameStore.questionIndex == 1"></Questions1>
        <Questions2 v-if="gameStore.questionIndex == 2"></Questions2>
        <Questions3 v-if="gameStore.questionIndex == 3"></Questions3>
        <Questions4 v-if="gameStore.questionIndex == 4"></Questions4>
        <Questions5 v-if="gameStore.questionIndex == 5"></Questions5>
        <Questions6 v-if="gameStore.questionIndex == 6"></Questions6>
        <Questions7 v-if="gameStore.questionIndex == 7"></Questions7>
        <Questions8 v-if="gameStore.questionIndex == 8"></Questions8>
    </div>
</template>

<script setup>
    const gameStore = useGameStore()
</script>

<style scoped>
    .monitor {
        width: 100%;
        height: 100%;
        background-color: black;
        border: 1px solid #00FF00;
        box-sizing: border-box;
    }

    p {
        padding-left: 5%;
        font-size: 1.8rem;
        color: rgb(0, 255, 0);
        margin: 0;
        margin-top: 20px;
        text-shadow: 0px 0px 3px rgb(0, 255, 0);
    }
</style>