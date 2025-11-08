<template>
    <div class="question__wrapper">
        <div class="question">
            <p class="text">
            Как называется редкий вид женского интимного пирсинга, при котором прокол делается с внутренней части влагалища в сторону анального отверстия. 
            </p>
        </div>
        <div class="input__wrapper">
            <input v-model="answer" class="input" type="text" name="" id="">
            <button @click="answerHandler" class="button">></button>
            <button @click="clueHandler" class="button">?</button>
            <div v-if="isClueActive" class="clue">
                <img src="/images/clue.png" class="img" alt="">
                <p class="text text--clue">По статистике треть людей голосуют за него</p>
            </div>
        </div>
    </div>
</template>

<script setup>
    const gameStore = useGameStore()

    const isClueActive = ref(false)
    const answer = ref('')

    function clueHandler() {
        isClueActive.value = !isClueActive.value
    }

    function answerHandler() {
        if (answer.value.toLowerCase() == 'фуршет') {
            gameStore.questionIndex += 1
            localStorage.setItem('questionIndex', gameStore.questionIndex)
        }
    }
</script>

<style scoped>
    .question__wrapper {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 90vh;
        width: 90%;
        margin: 0 auto;
    }

    .img {
        width: 150px;
    }

    .text, .input, .button {
        font-family: "Tiny5", sans-serif;
        font-size: 1.8rem;
        color: rgb(0, 255, 0);
        margin: 0;
        text-shadow: 0px 0px 3px rgb(0, 255, 0);
    }

    .text--clue {
        font-size: 1rem;
        margin-left: 20px;
        margin-right: 20px;
    }

    .button {
        border: 2px solid rgb(0, 255, 0);
        padding-left: 20px;
        padding-right: 20px;
        transition: 0.2s;
        cursor: pointer;
        background-color: black;
    }

    .button:hover {
        background-color: rgb(0, 255, 0);
        color: black;
        transform: scale(1.05);
        -webkit-box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
        -moz-box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
        box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
    }

    .button:active {
        transform: scale(0.95);
    }

    .text {
        padding-top: 20px;
    }

    .input__wrapper {
        position: relative;
        width: 100%;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .clue {
        box-sizing: border-box;
        border: 2px solid rgb(0, 255, 0);
        background-color: black;
        position: absolute;
        bottom: 100px;
        right: 0;
        display: flex;
        flex-direction: row;
    }

    .input {
        padding-left: 20px;
        background-color: black;
        border: 2px solid #00FF00;
        height: 60px;
        width: 80%;
        font-size: 1.8rem;
        color: rgb(0, 255, 0);
        margin: 0;
        text-shadow: 0px 0px 3px rgb(0, 255, 0);
    }    

    .input:focus {
        border: 2px solid #00FF00;
        outline: none;
    }
</style>