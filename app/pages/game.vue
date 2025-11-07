<template>
    <div class="screen">
        <audioplayer></audioplayer>
        <div class="wrapper">
            <div class="background">
                <Background />
            </div>
            <div class="text-field">
                <div class="text-field__wrapper">
                    <div class="buttons">
                        <button class="button" @click="previousLine"><</button>
                        <button class="button" @click="nextLine">></button>
                    </div>
                    <p class="text-field__text">
                        {{ str }}
                    </p>
                </div>
            </div>
            <div class="monitor" v-if="gameStore.isMonitorOpen">
                <GameMonitor />
            </div>
        </div>
    </div>
</template>

<script setup>
    const gameStore = useGameStore()
    const str = ref('')
    let interval = null

    function previousLine() {
        if (gameStore.lineIndex > 0) {
            localStorage.setItem('lineIndex', gameStore.lineIndex - 1)
            gameStore.lineIndex--
        }
    }

    function nextLine() {
        if (gameStore.lineIndex < gameStore.chapters[gameStore.chapterIndex].length - 1) {
            localStorage.setItem('lineIndex', gameStore.lineIndex + 1)
            gameStore.lineIndex++
        } else {
            gameStore.updateGameStatus()
        }
    }  

    watch(() => gameStore.chapters[gameStore.chapterIndex][gameStore.lineIndex].line, async (newLine) => {
        str.value = ''
        if (interval) {
            clearInterval(interval)
        }
        let line = newLine.split('')
        let letterIndex = 0
        interval = setInterval(() => {
            if (letterIndex < line.length) {
                str.value += line[letterIndex]
                letterIndex += 1
            } else {
                clearInterval(interval)
            }
        }, 40)
    }, { immediate: true })
</script>

<style scoped>
    .screen {
        width: 100%;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .wrapper {
        width: 70%;
        position: relative;
    }

    .background {
        height: 80vh;
        margin: 0 auto;
    }

    .text-field {
        margin-top: 2vh;
        height: 16vh;
        background-color: black;
        position: relative;
    }

    .text-field__wrapper {
        box-sizing: border-box;
        height: 100%;
        border: 1px solid rgb(0, 255, 0);
                -webkit-box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
        -moz-box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.05);
        box-shadow: 0px 0px 11px 8px rgba(0, 255, 0, 0.0);
    }

    .text-field__text {
        width: 90%;
        font-size: 1.8rem;
        margin-top: 15px;
        color: rgb(0, 255, 0);
        padding-left: 20px;
        text-shadow: 0px 0px 3px rgb(0, 255, 0);
    }

    .buttons {
        position: absolute;
        right: 10px;
        display: flex;
        width: 10%;
        justify-content: space-between;
        bottom: 10px;
    }

    .button {
        font-family: "Tiny5", sans-serif;
        font-weight: 400;
        font-style: normal;
        font-size: 3rem;
        width: 60px;
        height: 60px;
        background-color: black;
        color: rgb(0, 255, 0);
        transition: 0.2s;
        border: 1px solid rgb(0, 255, 0);
        cursor: pointer;
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

    .monitor {
        position: absolute;
        z-index: 20;
        width: 100%;
        height: 98vh;
        top: 0.5vh;
    }
</style>