<template>
    <div class="audio">
        <audio ref="audio" src="/music/back.mp3" autoplay loop></audio>
        <button @click="clickHandler">
            <img v-if="isPlay" src="/images/soundOn.png" alt="">
            <img v-if="!isPlay" src="/images/soundOff.png" alt="">
        </button>
    </div>
</template>

<script setup>
    const audio = ref(null)
    const isPlay = ref(false)
    onMounted(async () => {
        await nextTick()
        if (audio.value) {
            audio.value.volume = 0.1
            isPlay.value = true
            audio.value.play().catch(err => {
                console.log('Автозапуск заблокирован браузером', err)
                isPlay.value = false
            })
        } else {
            isPlay.value = false
        }
    })

    function clickHandler() {
        if (isPlay.value) {
            audio.value.pause()
            isPlay.value = false
        } else {
            audio.value.volume = 0.1
            audio.value.play()
            isPlay.value = true
        }
    }

</script>

<style scoped>
    .audio {
        position: absolute;
        top: 20px;
        left: 20px;
    }

    button {
        width: 50px;
        height: 50px;
        border: 1px solid #00FF00;
        padding: 10px;
        background-color: black;
        cursor: pointer;
    }

    img {
        width: 100%;
        image-rendering: smooth;
    }

</style>