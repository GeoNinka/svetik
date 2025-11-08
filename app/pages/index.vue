<template>
    <div class="wrapper">
        <p class="heading">SVETLASHKIS THE GAME</p>
        <img class="img" src="/images/sveta.png" alt="">
        <NuxtLink to="/game" v-if="gameStore.chapterIndex != 0 || gameStore.lineIndex != 0" class="button">Продолжить</NuxtLink>
        <NuxtLink to="/game" v-if="gameStore.chapterIndex == 0 && gameStore.lineIndex == 0" class="button">Новая игра</NuxtLink>
        <button @click="resetProgress" class="button" v-if="gameStore.chapterIndex != 0 || gameStore.lineIndex != 0">Сбросить прогресс</button>
    </div>
</template>

<script setup>
    const gameStore = useGameStore()

    function resetProgress() {
        localStorage.removeItem('questionIndex')
        localStorage.removeItem('chapterIndex')
        localStorage.removeItem('lineIndex')
        localStorage.removeItem('isMonitorOpen')
        gameStore.questionIndex = 1
        gameStore.chapterIndex = 0
        gameStore.lineIndex = 0
        gameStore.isMonitorOpen = false

    }
</script>

<style scoped>
    .wrapper {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-top: 10vh;
    }

    .img {
        width: 500px;
        margin-top: 40px;
        margin-bottom: 40px;
        animation: floating 6s ease-in-out infinite;
    }

    .button, .heading {
        font-size: 2rem;
        text-decoration: none;
        color: rgb(0, 255, 0);
        text-shadow: 0px 0px 6px rgb(0, 255, 0);
        margin: 0;
    }

    .heading {
        font-size: 4rem;
        animation: heartbeat 1.7s ease-in-out infinite;
    }

.button {
        font-family: "Tiny5", sans-serif;
        font-weight: 400;
        font-style: normal;
        font-size: 2rem;
        border: 1px solid rgb(0, 255, 0);
        padding: 20px;
        transition: 0.2s;
        cursor: pointer;
        background-color: black;
        margin-top: 10px;
    }

    .button:hover {
        background-color: rgb(0, 255, 0);
        color: black;
        transform: scale(1.05);
        -webkit-box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
        -moz-box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
        box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
    }

    @keyframes floating {
        0%, 100% {
            transform: rotate(-5deg);
        }
        50% {
            transform: rotate(5deg);
        }
    }

    @keyframes heartbeat {
        0%, 60%, 100% {
            transform: scale(1);
        }
        30% {
            transform: scale(1.03);
        }
        59% {
            transform: scale(1);
        }
    }
</style>